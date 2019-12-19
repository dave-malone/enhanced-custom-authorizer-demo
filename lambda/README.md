DEPLOYMENT_BUCKET=mybucketname

# Package SAM template
sam package --template-file sam.yml --s3-bucket $DEPLOYMENT_BUCKET --output-template-file packaged.yml

# Deploy packaged SAM template
sam deploy --template-file ./packaged.yml --stack-name iot-enhanced-custom-authorizer-lambda-stack --capabilities CAPABILITY_IAM

# Get the ARN for the deployed function
aws cloudformation describe-stack-resources --stack-name iot-enhanced-custom-authorizer-lambda-stack
