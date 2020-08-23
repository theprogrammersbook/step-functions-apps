# step-functions-helllo-world

### install npm
  sudo apt-get install npm
### install serverless 
 sudo npm install -g serverless
##### -g means that we are telling to npm to install serverless in globally
## Create AWS NodeJs project template

nagaraju@nagaraju:~/Technology/Repository/theprogrammersbook/step-functions-helllo-world$ 
````sls create --template aws-nodejs````
Serverless: Deprecation Notice: Support for Node.js versions below v10 will be dropped with next major release. Please upgrade at https://nodejs.org/en/
            More Info: https://www.serverless.com/framework/docs/deprecations/#OUTDATED_NODEJS
Serverless: Generating boilerplate...
 _______                             __
|   _   .-----.----.--.--.-----.----|  .-----.-----.-----.
|   |___|  -__|   _|  |  |  -__|   _|  |  -__|__ --|__ --|
|____   |_____|__|  \___/|_____|__| |__|_____|_____|_____|
|   |   |             The Serverless Application Framework
|       |                           serverless.com, v1.79.0
 -------'

Serverless: Successfully generated boilerplate for template: "aws-nodejs"
Serverless: NOTE: Please update the "service" property in serverless.yml with your service name
nagaraju@nagaraju:~/Technology/Repository/theprogrammersbook/step-functions-helllo-world$ 
__

### npm init

npm init -y

### Add Serverless step funcitons
 npm i --save-dev serverless-step-functions

### Add Serverless step functions into serverless.ym file as plugin
```
plugins:
  - serverless-step-functions

```

### Add the following lines in serverless.yml file

```
stepFunctions:
  stateMachines:
    hello:
      name: hello
      definition:
        Comment: hello world example
        StartAt: SayHello
        States:
          SayHello:
            Type: Task
            Resource:
              Fn::GetAtt: [hello,Arn]
            End: true

```
### Update handler.js file as 

```

module.exports.hello = async name => {
  return 'hello ${name}'
};
``` 
### Deploy the application 
sls deploy

When deploy is running if you get error like AWS Credentials are missing then you can add the access key and secreat key of aws.
https://www.serverless.com/framework/docs/providers/aws/guide/credentials/
export AWS_ACCESS_KEY_ID=<your-key-here>
export AWS_SECRET_ACCESS_KEY=<your-secret-key-here>
#####AWS_ACCESS_KEY_ID and AWS_SECRET_ACCESS_KEY are now available for serverless to use
serverless deploy or sls deploy

#### How to run the applicaiton.
sls invoke stepf --name helloman --data 'Nagaraju'



### You can view the Step function in the AWS Console.

When you run the sls deploy -v  then we will get the following .
....
.....
..
.....
..
Stack Outputs
HelloLambdaFunctionQualifiedArn: arn:aws:lambda:us-east-1:323728230337:function:step-functions-hello-dev-hello:2

From the above we came to know that  our step functions are in us-east-1 region .
So that we can access the step functions with the following url;

https://us-east-1.console.aws.amazon.com/states/home?region=us-east-1#/statemachines

  

 
 
 
