# GAwS
A fork of [aws-apps-scripts](https://github.com/smithy545/aws-apps-scripts).
A script for calling the AWS API from Google Apps Script.

## How to use:

1. Create a new project in google scripts.
2. Copy paste aws.js into it's own file in your project and save it.
3. Open up a new a file and setup the AWS variable with AWS.init.
4. Use method for each service.

## Example:
### EC2

```javascript
function myFunction() {
  AWS.init('MY_ACCESS_KEY', 'MY_SECRET_KEY');
  Logger.log(AWS.ec2(
    'us-east-1', // region
    'DescribeInstances', // action
    {"Version":"2015-10-01"} // params
  ));
}
```

### S3
```javascript
function myFunction() {
  AWS.init('MY_ACCESS_KEY', 'MY_SECRET_KEY');
  Logger.log(AWS.s3(
    'us-west-2', // region
    'bucket', // bucket
    'key', // key
    'PUT', // method
    '{"key":"value"}' // payload
  ));
}
```

### Lambda
#### Sync
```javascript
function myFunction() {
  AWS.init('MY_ACCESS_KEY', 'MY_SECRET_KEY');
  Logger.log(AWS.lambdaInvoke(
    'us-west-2', // region
    'functionName', // functionName
    '{"key":"value"}' // payload
  ));
}
```

#### Async
```javascript
function myFunction() {
  AWS.init('MY_ACCESS_KEY', 'MY_SECRET_KEY');
  Logger.log(AWS.lambdaInvokeAsync(
    'us-west-2', // region
    'functionName', // functionName
    '{"key":"value"}' // payload
  ));
}
```
