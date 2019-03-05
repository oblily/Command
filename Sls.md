
# Serverless Framwork

## sls -V

Check version.

## sls deploy

[Detail](https://serverless.com/framework/docs/providers/aws/cli-reference/deploy/) \
deploy src. \
--stage or -s The stage in your service that you want to deploy to. \
--region or -r The region in that stage that you want to deploy to. \
--package or -p path to a pre-packaged directory and skip packaging step. \
--verbose or -v Shows all stack events during deployment, and display any Stack Output. \

# serverless invoke [local] --function functionName

Invokes deployed function. It allows to send event data to the function, read logs and display other important information of the function invocation.