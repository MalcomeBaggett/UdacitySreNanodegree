Creating an EKS Cluster - Web console
Creating a cluster and deploying an application are two separate things. First, we will learn to create a cluster. Like any other AWS service, an EKS cluster can be created using either of the following:

Web console
AWS CLI tool
We will learn to create a cluster using both the ways - web console and AWS CLI tool. We'll start with making you familiar with the web console.

If you are already familiar with creating an EKS cluster, you can skip this page and the one that follows.

Guided Instructions - Use the web-console
This is the outline for the step-by-step instructions that follow on this page.

Part 1 - Prerequisites
Create default VPC and subnets
Create IAM roles for cluster and worker nodes
Create SSH Key Pair
Part 2 - Creating an EKS Cluster
Create cluster in EKS
Create and specify role for Kubernetes cluster
Enable public access
Part 3 - Creating a Node Group
Add Node Group in the newly-created cluster
Create and specify role for IAM role for node group
Create and specify SSH key for node group
Set instance type to t3.micro for cost-savings as we learn how to use Kubernetes
Specify desired number of nodes
Part 4 - Clean Up
Delete the node group
Delete the cluster
Delete the custom IAM roles
Part 1. Prerequisites
Default VPC and subnets: A default VPC comprises a size /16 IPv4 CIDR block, providing up to 65,536 private IPv4 addresses. It automatically creates a size /20 default subnet in each Availability Zone. There are other components, such as default route tables, and internet gateway that are also created automatically. Go to the VPC service and check if you have a default VPC already set up in your account. (See the snapshot below). If no, refer to the Creating a default VPC instructions.
Screenshot of VPCs on AWS web console highlighting the Default VPC in orange on the right
A default VPC

IAM role for the cluster: A role is a set of permissions that can be assigned to an entity. You need to create the roles that your cluster and the node group will assume. To create a new role, go to the IAM service → Roles, and follow the steps below.
Create the role that the cluster (control plane) will assume in order to manage AWS resources on your behalf.

Click on the Create role button to start the wizard.
Choose AWS service as the trusted entity.
Click on the EKS to see EKS use cases. (See the snapshot below)
Choose EKS - Cluster. It will allow access to other AWS service resources that are required to operate clusters managed by EKS. Click Next.
The needed policy, AmazonEKSClusterPolicy, will be selected. This policy provides Kubernetes the permissions it requires to manage resources on your behalf.
Click Next, and ignore the Tags.
Click Next, and name the role something like myEKSClusterRole
Screenshot showing use case options for EKS, highlighting EKS - Cluster in orange
Select the EKS - Cluster use case while creating a role.

IAM role for the worker nodes: Create a new role, say myEKSWorkerNodeRole, that will give permissions to the kubelet running on the worker node to make calls to other APIs on your behalf. Follow the similar procedure as above, except choosing the EC2 use case instead of EKS. Also, in the Attach permissions policies section on the next page, search and choose the checkbox against the following policies:
AmazonEKSWorkerNodePolicy
AmazonEC2ContainerRegistryReadOnly
AmazonEKS_CNI_Policy
Finish creating the role. Need help? See the reference documentation.

SSH key pair: AWS generates a pair of RSA encrypted public and private keys that help log into the EC2 instance (virtual machines). The public key is placed automatically on the EC2 instances, whereas you use the private key instead of a password to access your instances securely. To create the key pair, go to the EC2 service → Network & Security → Key Pairs option on the left navigation tree.
Click on the Create key pair button.
Provide a name of your choice and choose the desired format. A .pem format is used by Mac/Linux users, and a .ppk format is used by Windows users.
It will download the private key file to your local.
Screenshot showing options to create a key pair, highlighting the name field and the use of pem as the file format, for use with OpenSSH
Create an SSH key pair

Part 2. Create an EKS Cluster
An EKS cluster comprises of:

A control plane consists of the nodes running the Kubernetes software, such as etcd and the Kubernetes API server. These components run in AWS-owned accounts.
A data plane made up of worker nodes. Worker nodes run in customer accounts.
Once your control plane is ready, you can attach a set of worker nodes to the control plane for running the pods. Let's create the control plane (EKS cluster) first.

Navigate to the EKS service → Amazon EKS → Clusters option on the left navigation tree. Click on the Create cluster button to launch the wizard, and use the following details:

Cluster configuration - Provide a name of your choice, say myEKSCluster, and choose the default Kubernetes version. Ensure to have selected the IAM role you created above. The cluster, after assuming the role, will manage AWS resources on your behalf.
Cluster configuration showing name, Kubernetes version, and the cluster service role
Cluster configuration

Specify networking - Choose the default VPC, subnets, and security group (firewall rules) you have in your account, and mark the cluster endpoints as publicly accessible.
Screenshot of Networking options, highlighting VPC info, subnets, security groups, and the Cluster endpoint access as Public
Specify networking

Error showing cannot create cluster because the targeted availability zone does not currently have sufficient capacity. This is a known issue.
Known issue

If you get an error that the cluster cannot be created because the targeted availability zone does not have sufficient capacity (as shown above), you can either wait a few minutes and try again, or remove the affected zone from the list of subnets.

Configure logging - Accept the defaults and create the cluster. It will take several minutes to create the cluster.
Part 3. Create a Node Group
A Node Group is a set of worker nodes (virtual machines) used to run the pods that your cluster will be serving.

Follow the steps below to create a Node Group and attach it to the Cluster:

Once your cluster shows an Active state, click on the cluster name to view more details.
Screenshot showing a cluster, including name, kubernetes version, and status (Active)
An Active cluster

Go to the Configuration → Compute section of your new cluster, and click on the Add Node Group button.
Screenshot showing how to add node group following the instructions provided above
The Add Node Group button.

Node Group configuration: Provide a name, and attach the myEKSWorkerNodeRole IAM role to the Node Group. According to AWS,
The IAM Role will give permissions to the kubelet running on the node to make calls to other APIs on your behalf.

Screenshot showing node group configuration, highlighting name and IAM Role
Node Group configuration

Node Group compute and scaling configuration: In this section, you choose the OS, (virtual) hardware configuration, and count of the worker nodes. Use the following values:
Field Value Purpose
AMI type Amazon Linux 2 (AL2_x86_64) OS
Capacity type On-Demand Instance purchasing option
Instance types t3.micro 2 vCPU, 1 GiB memory
Disk size 20 GiB ---
Scaling configuration
Min size 2 Min number of nodes for scaling in.
Max size 2 Max number of nodes for scaling out.
Desired size 2 Initial count

---

Screenshot showing node group compute and scaling configuration as defined in the table above
Node Group compute and scaling configuration

Node Group network configuration: Choose the subnets selected earlier while creating the cluster. Choose the SSH key pair created in the prerequisites section above. Also, allow remote access from anywhere on the Internet.
Screenshot showing network configuration based on the instructions provided above
Node Group network configuration

Review and finish creating the Node Group.
Screenshot showing verification of created cluster and node group, with active status
myEKSCluster → myNodeGroup

Screenshot showing that the node group now shows up in the cluster configuration details
myNodeGroup showing up in the cluster configuration details

Screenshot showing worker node details in the cluster overview
Worker node details

Screenshot showing the automatically created nodes in the EC2 service console
The two worker nodes created automatically by the Node Group, in the EC2 service.

Screenshot showing default components, workload, and applications running in the cluster, highlighting the deployment and Daemon set types, and the documentation available on the right hand side
Default components/workload/applications running in the cluster. Refer to the documentation for more details on the components' purpose.

Part 4. Clean up
Delete the Node Group. Explore how you'd do the deletion. If you need help, refer to the instructions here.

Delete the cluster. Need help, again? Refer to the instructions.

Delete the custom IAM roles you have created in this exercise.

Congratulation! You have learned to create a Kubernetes cluster. Moving forward, we will use a one-line command, eksctl, to do it all for us.
