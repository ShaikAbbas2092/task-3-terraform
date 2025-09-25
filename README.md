
This project demonstrates how to create and manage a Docker container using Terraform.

## Prerequisites

- Docker installed and running locally
- Terraform installed on your machine

## Basic Terraform Commands

- Initialize Terraform (install providers):
  ```
  terraform init
  ```
- Review planned changes before applying:
  ```
  terraform plan
  ```
- Apply the configuration to create the container:
  ```
  terraform apply
  ```
- List all managed resources:
  ```
  terraform state list
  ```
- Destroy resources created by Terraform:
  ```
  terraform destroy
  ```

## Example `main.tf` snippet

```
provider "docker" {}

resource "docker_image" "nginx" {
  name = "nginx:latest"
}

resource "docker_container" "nginx" {
  image = docker_image.nginx.image_id
  name  = "terraform-nginx-demo"
  ports {
    internal = 80
    external = 8080
  }
}
```

## How to use

1. Run `terraform init`
2. Run `terraform plan` to preview changes
3. Run `terraform apply` to create the Docker container
4. Access the running container on `http://localhost:8080`
5. Run `terraform destroy` when you want to remove the container

