# Ansible Installation Setup

This project provides a comprehensive setup for installing Ansible on both RHEL and Ubuntu systems. It also includes the configuration of AWS EC2 instances that will act as Ansible controllers and hosts. The following is a breakdown of the files and their purpose within the project:

## Files Overview

### 1. `ansible-install-rhel.sh`
This script automates the installation of Ansible on a RHEL-based system. It includes user creation, setting up Python 3, and installing Ansible via `pip`.

### 2. `ansible-install-ubuntu.sh`
This script installs Ansible on an Ubuntu-based system. It adds the Ansible PPA, creates the necessary user, and installs Ansible using `apt`.

### 3. `aws_ec2.yaml`
This YAML file is used to define the inventory for AWS EC2 instances using the `aws_ec2` plugin. It categorizes the instances based on specific tags and attributes.

### 4. `create_ansible_user_rhel.sh`
This script is designed to create a user named `ansible` on RHEL systems, configure password authentication, and restart the SSH service to apply changes.

### 5. `create_ansible_user_ubuntu.sh`
Similar to the RHEL script, this script sets up an `ansible` user on Ubuntu systems, adjusts SSH settings, and restarts the SSH service.

### 6. `data0.tf` and `data1.tf`
These Terraform data files are responsible for fetching the latest AMIs (Amazon Machine Images) for Ubuntu and RHEL. They filter AMIs based on criteria such as architecture, virtualization type, and root device type.

### 7. `ec2.tf`
This Terraform configuration file defines the resources for creating EC2 instances. It includes the Ansible controller instance and various Ubuntu and RHEL hosts, specifying instance types, IAM roles, and user data scripts.

### 8. `Instance-profile.tf`
This Terraform file sets up the necessary IAM roles and policies for the EC2 instances to interact with AWS services securely. It includes the creation of an IAM role, instance profile, and policy attachments.

### 9. `linux-ssh-script.tpl` and `windows-ssh-script.tpl`
These template files are used to configure SSH access on Linux and Windows systems. They generate SSH configuration entries for the Ansible user based on instance details.

### 10. `null-resource.tf`
This file defines a `null_resource` that runs local-exec commands to apply the SSH configuration templates after the EC2 instances are up and running. It also includes a delay to ensure instances are ready before executing the commands.

### 11. `outputs.tf`
This file defines Terraform output values that provide important details about the deployed infrastructure, such as public and private IPs of the EC2 instances.

### 12. `provider.tf`
This file specifies the required Terraform version and AWS provider configurations, ensuring compatibility with the project's infrastructure code.

### 13. `script.sh`
A helper script used to configure the Ansible user’s SSH access by copying the authorized keys from the Ubuntu user.

### 14. `variables.tf`
This file defines the input variables for the Terraform configuration, including AWS region, instance types, and key pair names.

### 15. `vscode-install.sh`
This script installs Visual Studio Code on an Ubuntu system, ensuring that the Ansible controller has a code editor available for managing playbooks and configurations.

## Usage

To use this project, you can clone the repository and execute the relevant scripts and Terraform commands based on your environment. The setup is designed to be flexible and can be adapted to different cloud and on-premise scenarios.
