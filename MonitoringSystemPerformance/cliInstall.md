Creating an EKS Cluster

To clarify, there are multiple ways in which you can create and delete EKS clusters:

EKS web-console - It may not automatically delete the associated resources, such as VPC, or subnets.
CloudFormation console - You can use this method to delete the cluster and the associated resources. We will learn this service later in this lesson.
EKSCTL utility - Recommended way
CloudFormation allows you to provision all the infrastructure resources that you will need using simple configuration (text) files, and we will learn to use CloudFormation to create other AWS resources, towards the end of this lesson. For creating an EKS cluster, AWS recommends using the EKSCTL utility.

Create an EKS Cluster using the EKSCTL tool

1. Create command
   Run the following command to create the EKS cluster:
   eksctl create cluster --name eksctl-demo --profile <profile-name>
   Known Issue - Sometimes, the cluster creation may fail in the us-east-1 region. In such a case, use --region=us-east-2 option.

It is because the us-east-1 region does not have sufficient capacity to support the cluster.

The command above will take a few minutes to execute, and create an EKS cluster "eksctl-demo" in the "us-east-1" region with:
One node group containing two m5.large nodes
Two subnets in separate availability zones
Two separate CloudFormation stacks - eksctl-eksctl-demo-cluster for the cluster, and eksctl-eksctl-demo-nodegroup-ng-7f9854c3 for the initial nodegroup
For more information on creating and managing clusters, refer here.

2. View progress
   Go to the CloudFormation console to view progress. If you don’t see any progress, be sure that you are viewing clusters in the same region that they are being created.
   For example, if eksctl is using region us-east-2, you’ll need to set the region to US East (Ohio) in the dropdown menu in the upper right of the console.

In case of issues, you can try:

eksctl utils describe-stacks --region=us-east-1 --cluster=eksctl-demo --profile <profile-name>
Screenshot showing how to verify the region in the AWS web console
Verify the region in the web-console.

Screenshot showing how to verify the region in the command line with the output from creating the cluster with the eksctl command. The line starting with "creating EKS cluster" shows the cluster name as well as the region.
Verify the region shown in the command line

Screenshot of CloudFormation on the AWS web console showing stacks created with eksctl command
CloudFormation stacks created as a part of EKSCTL command

3. View details
   Once the status is CREATE_COMPLETE in the CloudFormation web-console, fetching the details of the newly created cluster using:
   eksctl get cluster --name=eksctl-demo --region=us-east-2 --profile <profile-name>
   Go back to the CloudFormation web console and select the eksctl-eksctl-demo-cluster stack. Select the tab Template, this shows you the Cloudformation template that eksctl command used to create your EKS cluster. The Cloudformation template describes all of the resources and connections between them that are needed for a cluster. We will discuss Cloudformation templates more later in the course.

Click the View in Designer button. This will give you a visual representation of the resources that make up the stack created. Close and leave the designer.

Screenshot of web console showing template used by eksctl to create CloudFormation stack
EKSCTL internally uses the template above to create the CloudFormation stack.

You can also check the health of your clusters nodes using the command:
kubectl get nodes --profile <profile-name>
Did you see the difference in the usage of eksctl vs kubectl?

The former is used to create/delete/edit a cluster, whereas the latter is used to interact with the cluster.

4. Delete the cluster
   You can delete the cluster either from the CloudFormation web-console, or by using the EKSCTL command. Choose any one option from below:

From the CloudFormation web-console, select your stack and choose delete from the actions menu
Delete using the EKSCTL:
eksctl delete cluster eksctl-demo --profile <profile-name>
Note: We recommend you shut down every resource (e.g., EC2 instances, CloudFormation stack, or any other hosted service) on the AWS cloud immediately after the usage; otherwise, you will be billed even if the resources are not in "actual" use.

While it is important to delete the cluster immediately after usage, if you are moving on to the next page and setting up the EKS Cluster authentication immediately, you should wait to delete the cluster until the next page is completed.

Important Points:

Node-exporter is to be installed on the EC2 instance.
Eksctl is a command-line interface used for EKS clusters. Please visit the link to learn more.

Creating a EKS Cluster: Key Points
eksctl makes it easy to create a cluster and all of the resources needed to use it
kubectl communicates the clusters master system and can be used to interact with nodes, pods, and services
When deleting a cluster, use eksctl delete or the CloudFormation console to avoid leaving dangling resources
Summary of the CLI tools
Now that you have now been introduced to three command-line tools that you can use to work with AWS EKS services:

AWSCLI: This tool allows you to interact with a wide variety of AWS services, not just EKS. Although there are aws commands to create or modify EKS services, this is a much more manual approach than using the other options.
eksctl: This command line tool allows you to run commands against a Kubernetes cluster. This is the best tool for creating or deleting clusters from the command line since it will take care of all associated resources for you.
kubectl: This tool is used to interact with an existing cluster, but can’t be used to create or delete a cluster.
Additional Resource
Further Usage of EKSCTL from eksctl.io. This documentation includes common commands for creating and managing clusters.
Official Amazon documentation for creating your Amazon EKS cluster and worker nodes
