# Install Grafana Agent Integration with AWS Secret Manager

## Requirements
- Create IAM role for access the Secret Manager

## Add this policy from role

`{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "secretsmanager:GetResourcePolicy",
        "secretsmanager:GetSecretValue",
        "secretsmanager:DescribeSecret",
        "secretsmanager:ListSecretVersionIds"
      ],
      "Resource": [
        "arn:aws:secretsmanager:<REGION>:<ACCOUNT-ID>:secret:*"
      ]
    }
  ]
}
`
## Clone this repository

### Run the helm chart, below the example:
`helm upgrade -i grafana grafana-agent --create-namespace grafana -f values.yaml`

###### If your cluster to use fargate, then use the example/values-fargate.yaml