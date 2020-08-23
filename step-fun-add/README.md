### Serverless Frame work

https://github.com/serverless-operations/serverless-step-functions#commands

install npm
sudo apt-get install npm

install serverless
sudo npm install -g serverless

-g means that we are telling to npm to install serverless in globally
Create AWS NodeJs project template
nagaraju@nagaraju:~/Technology/Repository/theprogrammersbook/step-functions-helllo-world$ 
```sls create --template aws-nodejs``` 

Serverless: Deprecation Notice: Support for Node.js versions below v10 will be dropped with next major release. Please upgrade at https://nodejs.org/en/ More Info: https://www.serverless.com/framework/docs/deprecations/#OUTDATED_NODEJS Serverless: Generating boilerplate...

| _ .-----.----.--.--.-----.----| .-----.-----.-----. | || -| _| | | -| _| | -|_ --|__ --| |____ ||| _/||| ||||_____| | | | The Serverless Application Framework | | serverless.com, v1.79.0 -------'

Serverless: Successfully generated boilerplate for template: "aws-nodejs" Serverless: NOTE: Please update the "service" property in serverless.yml with your service name nagaraju@nagaraju:~/Technology/Repository/theprogrammersbook/step-functions-helllo-world$ __

### npm init
npm init -y

#### Add Serverless step funcitons
npm i --save-dev serverless-step-functions

#### Add Serverless step functions into serverless.ym file as plugin
plugins:
  - serverless-step-functions


### After writing the code 

### Deploy
sls deploy

### Run the code

nagaraju@nagaraju:~/Technology/Repository/theprogrammersbook/step-functions-apps/step-fun-add$ sls invoke stepf --name simple-maths --data '{"x":42,"y":20}'
Serverless: Deprecation Notice: Support for Node.js versions below v10 will be dropped with next major release. Please upgrade at https://nodejs.org/en/
            More Info: https://www.serverless.com/framework/docs/deprecations/#OUTDATED_NODEJS
````
{ executionArn: 'arn:aws:states:us-east-1:323728230337:execution:simple-maths:03f96e93-5ff0-4dd6-a9df-6b0c34ac1fee',
  stateMachineArn: 'arn:aws:states:us-east-1:323728230337:stateMachine:simple-maths',
  name: '03f96e93-5ff0-4dd6-a9df-6b0c34ac1fee',
  status: 'SUCCEEDED',
  startDate: 2020-08-23T14:03:25.625Z,
  stopDate: 2020-08-23T14:03:26.311Z,
  input: '{"x":42,"y":20}',
  output: '124' }
````
nagaraju@nagaraju:~/Technology/Repository/theprogrammersbook/step-functions-apps/step-fun-add$ 

### You can view the Step function in the AWS Console.

When you run the sls deploy -v  then we will get the following .
....
.....
..
.....
..
Stack Outputs
AddLambdaFunctionQualifiedArn: arn:aws:lambda:us-east-1:323728230337:function:step-functions-simple-math-dev-add:2
DoubleLambdaFunctionQualifiedArn: arn:aws:lambda:us-east-1:323728230337:function:step-functions-simple-math-dev-double:2
SimpleDashmathsDashfunctionsArn: arn:aws:states:us-east-1:323728230337:stateMachine:simple-maths-functions
ServerlessDeploymentBucketName: step-functions-simple-ma-serverlessdeploymentbuck-8gtsonsy6cul

From the above we came to know that  our step functions are in us-east-1 region .
So that we can access the step functions with the following url;

https://us-east-1.console.aws.amazon.com/states/home?region=us-east-1#/statemachines

  