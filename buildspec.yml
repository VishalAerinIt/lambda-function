version: 0.2

phases:
  install:
    runtime-versions:
      python: 3.11
    commands:
      - echo Installing dependencies...
      - pip install -r requirements.txt -t .
  build:
    commands:
      - echo Zipping Lambda function...
      - zip -r function.zip .
  post_build:
    commands:
      - echo Uploading to S3...
      - aws s3 cp function.zip s3://lambda-function-vishal/lambda/function.zip
      - echo Updating Lambda function...
      - aws lambda update-function-code \
          --function-name HelloWorldFunction \
          --s3-bucket lambda-function-vishal \
          --s3-key lambda/function.zip
