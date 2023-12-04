curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp

sudo mv /tmp/eksctl /usr/local/bin

for cloud shell use the below command

mkdir -p ~/.local/bin && mv /tmp/eksctl ~/.local/bin

4. Helm
Helm is a package manager for Kubernetes applications.

If you are using Cloud Shell, first run:

export HELM_INSTALL_DIR=~/.local/bin
Copy
If for some reason you skipped the previous step, you will have to create the ~/.local/bin directory.
Openssl is a requirement for Helm. Install it by running:

sudo yum install openssl -y
Copy
Alternatively, if you don’t use yum, you can use sudo apt install openssl -y, brew install openssl, or your package manager of choice.

If you don’t want to install openssl, you can disable Helm’s installer checksum verification using export VERIFY_CHECKSUM=false.
To install Helm, run:

curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash


# Install steps part deux
Step 0. Initial Installations
Create an EKS Cluster in us-east-2

Install helm

Install kubectl

Install AWS CLI

Step 1. Install Prometheus using Helm
Add the Helm repo and update the repo definition.

helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
Update Kubeconfig

## aws eks --region us-east-2  update-kubeconfig --name <cluster name>
aws eks --region us-east-2 update-kubeconfig --name prometheus-grafana-cluster
If you have set up your EKS cluster in a different region or with a different name, ensure that the aws eks command matches your EKS cluster setup.

Step 2. Create a namespace called monitoring
Create the monitoring namespace.

kubectl create namespace monitoring
Check the Kubernetes client and server version.

kubectl version --short
The version difference between client (1.26) and server (1.25) should NOT exceed the minor version skew of +/-1. Otherwise, consider upgrading the kubectl to a specific version. The instructions to upgrade are also available in the kubectl docs.

Step 3. Install kube-prometheus-stack
Use the command below to install the kube-prometheus-stack

helm install \
	[RELEASE_NAME] prometheus-community/kube-prometheus-stack \
    -f "[Path to the values.yaml]" \
    --namespace monitoring
In the command above, replace these placeholders:

[RELEASE_NAME] with the specific kube-prometheus release version compatible with your Kubernetes server version. To check the compatibility between your Kubernetes server version and the kube-prometheus-stack version, refer to the Compatibility matrix to know which release version is suitable for you.

[Path to the values.yaml] with the specific values.yaml for the selected kube-prometheus-stack version.

For example, the command below will install the latest kube-prometheus compatible with Kubernetes 1.27. Also, notice the path to the values.yaml used in the command below. You must switch to the desired kube-prometheus version in the Github repository and use the corresponding values.yaml.

helm install \
	prometheus prometheus-community/kube-prometheus-stack \ 
	-f "https://raw.githubusercontent.com/prometheus-community/helm-charts/main/charts/kube-prometheus-stack/values.yaml" \
    --namespace monitoring
Note: The values.yaml file is also attached in the resources section. The values file is used by the helm. Helm reads the values from this file and populates parameterized files with the appropriate values. We reference values.yaml file with the -f flag.

A screenshot displaying how to check the Kubernetes version and install the **kube-prometheus** chart. 
A screenshot displaying how to check the Kubernetes version and install the kube-prometheus chart.

Step 4. Run the commands to install Prometheus & Grafana
If you are not using Lens, use the kubectl port-forward command e.g.

kubectl get svc -A
kubectl port-forward service/prometheus-grafana 8080:80 -n monitoring
To view Grafana in the browser use localhost:8080.

Access the Grafana using the credentials:

username: admin 
password: prom-operator
Access the Grafana portal
Access the Grafana portal

Step 5. Install node_exporter
After ssh-ing into your EC2 instance, you will use the following commands to install node_exporter.

sudo useradd --no-create-home --shell /bin/false node_exporter
wget https://github.com/prometheus/node_exporter/releases/download/v1.2.2/node_exporter-1.2.2.linux-amd64.tar.gz
tar xvfz node_exporter-1.2.2.linux-amd64.tar.gz
sudo cp node_exporter-1.2.2.linux-amd64/node_exporter /usr/local/bin
sudo chown node_exporter:node_exporter /usr/local/bin/node_exporter
sudo nano /etc/systemd/system/node_exporter.service

[Unit]
Description=Node Exporter
Wants=network-online.target
After=network-online.target

[Service]
User=node_exporter
Group=node_exporter
Type=simple
ExecStart=/usr/local/bin/node_exporter

[Install]
WantedBy=multi-user.target

sudo systemctl daemon-reload
sudo systemctl enable node_exporter
sudo systemctl start node_exporter
sudo systemctl status node_exporter

sudo ufw allow 9100/tcp
sudo systemctl restart ufw