## We can create S3 bucket via crossplane via the following ways:

- Using a Simple Crossplane Manifest
- By Injecting Existing Terraform S3 module to Crossplane Manifest.
- Using a Custom Resource Definition as per our needs , basically like a module for different teams which can be claimed through an XRC(Claim).

## In this demo 1 I will use simple crossplane manifest. 

What is required - AWS provider manifest.

AWS Provider Manifest: This will Install all the CRD’s ( Custom Resources Definitions ) required to create resources on the cloud. Ex: rdsinstances.database.aws.crossplane.io,ec2.aws.crossplane.io/v1alpha1, etc.
You will have to run the following AWS manifest alone to install AWS and Terraform Modules:

1. run crossplane-s3/aws-provider.yaml (kubectl apply -f crossplane-s3/aws-provider.yaml)
2. We should create a secret for the AWS creds and all the required credentials like Github etc through a manifest.

    - Generate the configuration files with the AWS Credentials. 
    AWS_PROFILE=default && echo -e "[default]\naws_access_key_id = $(aws configure get aws_access_key_id --profile $AWS_PROFILE)\naws_secret_access_key = $(aws configure get aws_secret_access_key --profile $AWS_PROFILE)" > aws-creds.ini

    - Create a Kubernetes secret with the configuration file generated. 
    kubectl create secret generic aws-secret-creds -n crossplane-system --from-file=creds=./aws-creds.ini
3. ProviderConfig Manifest: This will inject secret required for the Crossplane to create resources in the Cloud.
    
    - kubectl apply -f providerconfig.yaml

4. Resource manifest 

    - kubectl apply -f crossplane-s3/s3.yaml

## In this demo 2 I will inject existing Terraform S3 module to Crossplane manifest 

There are two ways to do this :
1. By Injecting the Terraform s3 resource module as an Inline to the Crossplane Manifest.

2. By Injecting the Terraform s3 resource module which is in a Github repo as a Remote Source to the Crossplane Manifest.

I will do it by Injecting the Terraform s3 resource module as an Inline to the Crossplane Manifest.

As we have already installed the Required components like AWS & Terraform Provider, Secrets and ProviderConfig in the previous steps. We can now directly run the Inline template using

 “kubectl apply -f crossplane-terraform-s3/inline.yaml”

 