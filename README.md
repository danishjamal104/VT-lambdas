# VT-lambdas

Repository for AWS Lambda scripts

## How to use setup.py for managing lambdas

- Each lambda reside in a separate folder which is a node project hence we are using python script to create, build and list the lambdas.
- Location: [lambdas/setup.py](/lambdas/setup.py)
- Requirements
  - Terminal/Command promt
  - Python 3.x
  - python added as a path variable. To check run command `python --version`
- Run `python setupy.py`
- Available options

  - `--help` or `-h`: returns the docstring describing the available options and their arguments.
  - `--init` or `-i`: creates new lambda by taking various input form user.
  - `--build` or `-b`:
    - build and generate the artifact as `[lambda-name].zip` in `../out` directory.
    - Pass `.` as argument to build all the lambdas or specific path to build a single lambda.
    - Example `python setup.py -b .` or `python setup.py -b user_access_patterns/lambda_for_createUser`
  - `--ls` or `-ls`: lists all the lambdas available/created.

  ## Testing the lambdas locally

  - Set up dynamo db using the [CreateTable.js](/DynamoDB/CreateTable.js) file.
  - For setting up dynamodb on aws, create `keys.json` file in the location mentioned. The content of keys.json file are shown below. Set up your aws IAM role accessKeyId and secretAccessKey in the file. Change the region to `ap-south-1`

  ```JSON
  { "accessKeyId": "<YOUR_ACCESS_KEY_ID>",
  "secretAccessKey": "<YOUR_SECRET_ACCESS_KEY>",
  "region": "<REGION>" }
  ```

* For setting dynamodb locally, comment out the local setup code as mentioned in CreateTable.js file
* All the lambdas can be tested locally using serverless or aws SAM or docker.

**Using docker images:**
Testing the lambda locally using docker requires a docker image file. If you are new to docker, refer the official documentation.

- Creating `Dockerfile` aws [documentation](https://docs.aws.amazon.com/lambda/latest/dg/images-create.html).
- Testing lambda using Dockerfile [documentation](https://docs.aws.amazon.com/lambda/latest/dg/images-test.html).

**Using aws SAM:**
SAM (Serverless Application Model) is an aws service which provides interface for testing and debugging.

- Getting started with [SAM](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-getting-started.html)
- Refer local function invokation [documentation](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-cli-using-invoke.html) for SAM.

**Using serverless:**
Serverless is an open source project that allows creation, deployment and testing of serverless applications.

- Installing and setting up [serverless](https://www.serverless.com/framework/docs/getting-started/)
- Copy the lambda to be tested in the serverless project directory.
- use `serverless invoke local` command to test your lambdas locally. Refer the [documentation](https://www.serverless.com/framework/docs/providers/aws/cli-reference/invoke-local/)

## Swagger API documentation

https://app.swaggerhub.com/apis/code-gambit/V-Transfer/1.0.0
