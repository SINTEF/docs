# Ansible or Terraform

You can use both [Ansible](https://www.ansible.com/) and [Terraform](https://www.terraform.io/).

They are two tools to automate the deployment of your infrastructure with code, and you can do the same operations with both. However, they do not have precisely the same purposes.

Terraform is better to manage resources in the cloud, such as creating VMs, creating load balancers, or object storage. You can do that with Ansible, but Terraform provides a better user experience.

Ansible is better to configure the resources and do system administration, such as installing software, editing configuration files, or running security updates. You can also do that with Terraform, but it provides a terrible user experience for this usage.

[Small tools exist](https://github.com/adammck/terraform-inventory) to link Terraform state files to Ansible inventory if you have large dynamic infrastructures.

## What about Chef or Puppet compared to Ansible?

Chef and Puppet are alternatives to Ansible, but I would recommend using Ansible over them. Ansible has a better architecture where you push your actions to the machine, only using SSH and Python. It is more accessible, more popular, and has more community support. You can find many comparisons online.

## Kubernetes replaces Ansible

Your software deployments should use Kubernetes whenever possible. Once you use Kubernetes, Ansible is a bit less frequently used because you use Kubernetes for most of your software deployments and configuration.

You still need Ansible to manage your Kubernetes hosts if you don't use a fully-managed Kubernetes cluster in the cloud. When you use fully-managed Kubernetes clusters in the cloud, you can use Terraform to manage them, but you may not have to use Ansible at all.