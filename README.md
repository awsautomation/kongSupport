# kongSupport

   KONG Enterprise Terraform Module - Execution Error
   
1. This Error i am getting while running Kong Enterprise -Terraform Module as in error it showing that this parameters already exist but its never exist before running this Kong Terraform Module as i have verified from AWS console. It is getting created only after running the Kong Terraform Module " main.tf" file.
then why this error is always occuring. Please Give the sophisticated solutions for this Kong Terraform module ASAP.

Error: Error creating DB Parameter Group: DBParameterGroupAlreadyExists: Parameter group kong-dev already exists
        status code: 400, request id: 80be5aea-da61-4221-a505-23e97388b751

  on .terraform/modules/kong/rds.tf line 38, in resource "aws_db_parameter_group" "kong":
  38: resource "aws_db_parameter_group" "kong" {

Error: Error creating Cache Parameter Group: CacheParameterGroupAlreadyExists: Parameter group kong-dev already exists
        status code: 400, request id: 30750629-c593-4911-8f31-57232b5fc981

  on .terraform/modules/kong/redis.tf line 29, in resource "aws_elasticache_parameter_group" "kong":
  29: resource "aws_elasticache_parameter_group" "kong" {

Error: Error creating Security Group: InvalidGroup.Duplicate: The security group 'kong-dev-postgresql' already exists for VPC 'vpc-033766c6b63d69bce'
        status code: 400, request id: ee9c72be-dadf-488c-9302-ac03941bd5c0

  on .terraform/modules/kong/security.tf line 2, in resource "aws_security_group" "postgresql":
   2: resource "aws_security_group" "postgresql" {

Error: AlreadyExistsException: An alias with the name arn:aws:kms:me-south-1:798545105402:alias/kong-dev already exists

  on .terraform/modules/kong/ssm.tf line 15, in resource "aws_kms_alias" "kong":
  15: resource "aws_kms_alias" "kong" {
  
  
2. MAIN.TF (Main.tf file for running kong Enterprise - Terraform module, is as it is, just i have given blank parameters due to security but while running i will assign the parameter to the main.tf for installations of Kong Enterprise Module).

provider "aws" {
region =""
access_key =""
secret_key=""
profile = "dev"
}

module "kong"{
source = "github.com/Kong/kong-terraform-aws"

vpc =""
environment = "dev"
ec2_ami = {
  me-south-1 = ""
}
ec2_instance_type =""
db_instance_class =""
ec2_key_name =""
ssl_cert_eternal =""
ssl_cert_internal =""
ssl_cert_admin=""
ssl_cert_manager=""
ssl_cert_portal=""

public_subnets =""
default_security_group=""
db_subnets =""

tags = {
owners =""
Team =""
}

}


