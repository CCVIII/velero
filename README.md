# velero

install velero 

get list cluster and name:

aws eks list-clusters --region eu-west-1

Leumi-Mortgage-eks-prd

1. Set the following environment variables:

# The name of the EKS cluster
EKS_CLUSTER_NAME=<name_of_eks_cluster>

# The service account and namespace where Velero will be installed
NAMESPACE=velero
SERVICE_ACCOUNT=velero

# The ID of the AWS account
AWS_ACCOUNT_ID=$(aws sts get-caller-identity --query "Account" --output text)
# The region of the EKS cluster
AWS_REGION="eu-west-1"

# The IAM OIDC provider of the EKS cluster
OIDC_PROVIDER=$(aws eks describe-cluster --name $EKS_CLUSTER_NAME --region $AWS_REGION --query "cluster.identity.oidc.issuer" --output text | sed -e "s/^https:\/\///")

# The name of the S3 bucket that will be created to store Velero backups
BUCKET=<name_of_s3_bucket>

# The name of the IAM role that will be created for Velero
VELERO_ROLE=<name_of_velero_iam_role
