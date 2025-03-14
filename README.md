# terraform-eks-setup
Terraform EKS Cluster Setup

This repository contains Terraform code for deploying a Amazon Elastic Kubernetes Service (EKS) cluster on AWS.

## Prerequisites

Before you begin, ensure you have the following installed and configured:

* **Terraform:** Install Terraform from [terraform.io](https://www.terraform.io/downloads).
* **AWS CLI:** Install and configure the AWS CLI with appropriate credentials. Ensure you are using AWS CLI version 2 or greater.
* **kubectl:** Install `kubectl` to interact with your Kubernetes cluster.
* **AWS Account:** You will need an active AWS account with sufficient permissions to create resources.

## Getting Started

1.  **Clone the Repository:**

    ```bash
    git clone <your_repository_url>
    cd <your_repository_directory>
    ```

2.  **Configure AWS Credentials:**

    * Ensure your AWS CLI is configured with the necessary credentials. You can use `aws configure` to set up your credentials.
    * If using AWS profiles, ensure the correct profile is being used.

3.  **Initialize Terraform:**

    ```bash
    terraform init
    ```

4.  **Review and Customize Variables:**

    * Customize the variables in `variables.tf` or create a `terraform.tfvars` file to override the default values. For example:

        ```terraform
        # terraform.tfvars
        aws_region = "us-east-1"
        eks_node_desired_size = 3
        ```

5.  **Plan and Apply:**

    * Create a Terraform execution plan:

        ```bash
        terraform plan
        ```

    * Apply the changes to create the EKS cluster:

        ```bash
        terraform apply
        ```

6.  **Configure kubectl:**

    * After the cluster is created, Terraform will output the `kubeconfig` file contents.
    * You can save the outputted `kubeconfig` to a file, or use the aws cli to update your local kubeconfig.

    ```bash
    aws eks update-kubeconfig --name <your_eks_cluster_name> --region <your_aws_region> --profile <your_aws_profile>
    ```

    * Replace `<your_eks_cluster_name>`, `<your_aws_region>`, and `<your_aws_profile>` with your cluster's details.

7.  **Verify kubectl Connection:**

    * Verify that `kubectl` is configured correctly:

        ```bash
        kubectl get nodes
        ```

## Cleanup

To destroy the EKS cluster and associated resources, run:

```bash
terraform destroy


Repository Structure

├── main.tf        # Main Terraform configuration
├── variables.tf   # Variable definitions
├── terraform.tfvars # (Optional) Variable overrides
└── README.md      # This file
