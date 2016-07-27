# DCOS Templates

Single / Multi-master templates for DCOS with updates for AWS GovCloud and NFS support.

## Usage

Single-master templates are provided for AWS GovCloud and NFS support, while multi-master templates are not
available currently with NFS support.

These templates are too large to be passed using template_body, so they must be uploaded to S3 for consumption. 
The following commands will upload and initiate the stack using the AWS CLI:

```
aws s3 cp 1.7/single-master.cloudformation-gov-nfs.json s3://your-s3-bucket/
aws cloudformation create-stack --stack-name your-dcos-stack --capabilities CAPABILITY_IAM --parameters ParameterKey=KeyName,ParameterValue=your-dcos-key-name --template-url https://s3.amazonaws.com/your-s3-bucket/single-master.cloudformation-gov-nfs.json
```

Be sure to replace the `your-s3-bucket`, `your-dcos-stack` and `your-dcos-key-name` placeholder values with the
appropriate ones for your account. It is up to you to have already created the bucket and key pairs in your account.