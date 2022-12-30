
# backend for subatomic payments

## setup AWS CLI:
https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html

Edit `~/.aws/credentials` with:
```
[default]
aws_access_key_id = <YOUR AWS ACCESS KEY>
aws_secret_access_key = <YOUR AWS SECRET ACCESS KEY>
region=us-west-2
```

## install / update / uninstall the REST endpoint into AWSA Lambda
```
# To create the REST API stack:
aws cloudformation create-stack \
  --stack-name subatomic-payments-rest-api \
  --template-body file://rest-api.yml \
  --capabilities CAPABILITY_NAMED_IAM

# To monitor the REST API's deployment:
aws cloudformation describe-stack-events \
  --stack-name subatomic-payments-rest-api

# After it's deployed, you can get your Lambda's public URL with:
aws cloudformation describe-stacks \
  --stack-name subatomic-payments-rest-api \
  --query "Stacks[0].Outputs[?OutputKey=='ApiUrl'].OutputValue" \
  --output text

# Append /hello_world to the URL, and hit it!
curl <your Lambda's public URL>/hello_world

# to delete:
aws cloudformation delete-stack --stack-name subatomic-payments-rest-api

# to update:
aws cloudformation update-stack \
  --stack-name subatomic-payments-rest-api \
  --template-body file://rest-api.yml \
  --capabilities CAPABILITY_NAMED_IAM
```


