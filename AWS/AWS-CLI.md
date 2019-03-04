
# Official Reference

[Official Reference](https://docs.aws.amazon.com/zh_cn/cli/latest/reference/index.html#cli-aws)

# aws configure

aws　環境設定
--profile XX　プロファイルXXの作成
> AWS Access Key ID [None]: XXXXXXXXXXXX \
> AWS Secret Access Key [None]: XXXXXXXXXXX \
> Default region name [None]: us-east-1 \
> Default output format [None]: json

# aws sts get-caller-identity | grep Account | awk '{print $2}' | sed -e "s/[^0-9]//g"

アカウントIDの取得/確認

# Lambda

## aws lambda create-function

Lambda関数の作成

mkdir test-function

cd test-function

vim index.js

zip -r test-function.zip .

aws lambda create-function \
  --function-name test-function \
  --runtime nodejs6.10 \
  --role arn:aws:iam::xxxxxxxxxxxx:role/xxxxxxxx \
  --handler index.handler \
  --zip-file fileb://test-function.zip

## aws lambda update-function-code

Lambda関数コードの変更

rm -rf test-function.zip && \

zip -r test-function.zip . && \

aws lambda update-function-code --function-name test-function --zip-file fileb://test-function.zip

## aws lambda delete-function

Lambda関数の削除

aws lambda delete-function \
 --function-name test-function \
 --region ap-northeast-1 \
--profile developper

## aws lambda invoke

Lambda関数の実行

aws lambda invoke \
--invocation-type RequestResponse \
--function-name helloworld \
--region ap-northeast-1 \
--log-type Tail \
--payload '{"key1":"value1", "key2":"value2", "key3":"value3"}' \
--profile developper \
outputfile.txt

# DynamoDB

## aws dynamodb list-tables

テーブル一覧

## aws dynamodb create-table

テーブル作成

aws dynamodb create-table  \
    --profile developper \
    --table-name Books \
    --attribute-definitions \
        AttributeName=id,AttributeType=S \
        AttributeName=isbn,AttributeType=S \
        AttributeName=title,AttributeType=S \
    --key-schema AttributeName=id,KeyType=HASH AttributeName=isbn,KeyType=RANGE \
    --provisioned-throughput ReadCapacityUnits=1,WriteCapacityUnits=1 \
    --global-secondary-indexes IndexName=title-index,KeySchema=[{AttributeName=title,KeyType=RANGE}],Projection={ProjectionType=KEYS_ONLY},ProvisionedThroughput={ReadCapacityUnits=1,WriteCapacityUnits=1}

※ --endpoint-url <http://localhost:8000/> をつければ ローカルの DynamoDB も作れる。

DDLを使用してテーブル作成

aws dynamodb create-table  --cli-input-json file://books.json

## aws dynamodb delete-table

テーブル削除

aws dynamodb delete-table  --table-name Books

## aws dynamodb scan --table-name XX

テーブル検索(全件検索)

aws dynamodb scan --table-name Books

## aws dynamodb query

テーブル検索(キー指定) --key-condition-expression

aws dynamodb query --endpoint-url <http://localhost:8000/>
--table-name ExampleTable \
--key-condition-expression ' key1 = :key1 AND key2 = :key2' \
--expression-attribute-values '{ ":key1": {"S":"A"}, ":key2": {"S":"01"} }'

テーブル検索(グローバルセカンダリインデックスを使用して検索)

aws dynamodb query --endpoint-url <http://localhost:8000/> --table-name ExampleTable \
  --index-name gsicol1-index \
  --key-condition-expression 'gsiCol1 = :gsiCol1' \
  --expression-attribute-values '{ ":gsiCol1": {"S":"A01-01"} }'

## aws dynamodb put-item

データ登録

aws dynamodb put-item --endpoint-url <http://localhost:8000/> --table-name ExampleTable \
  --item '{ "key1" : { "S" : "A"}, "key2" : { "S" : "01"}, "col1" : { "S" : "value1"}, "col2" : { "S" : "value2"} }'

## aws dynamodb update-item

データ更新

aws dynamodb update-item --endpoint-url <http://localhost:8000/> --table-name ExampleTable \
  --key '{ "key1": {"S":"A"}, "key2": {"S":"01"} }' \
  --update-expression 'SET col1 = :col1' \
  --expression-attribute-values '{ ":col1": {"S":"value1-update!"} }'

## aws dynamodb delete-item

データ削除

aws dynamodb delete-item --endpoint-url <http://localhost:8000/> --table-name ExampleTable \
  --table-name ExampleTable \
  --key '{ "key1": {"S":"A"}, "key2": {"S":"01"} }'

# Kinesis

## aws kinesis create-stream

ストリームの作成

aws kinesis create-stream --stream-name Foo --shard-count 1

## aws kinesis put-record

ストリームにレコードを入力する

aws kinesis put-record --stream-name Foo --partition-key 123 --data testdata

## aws kinesis get-shard-iterator

ストリームからレコードを取得する

aws kinesis get-shard-iterator --shard-id shardId-000000000000 --shard-iterator-type TRIM_HORIZON --stream-name Foo

## aws kinesis delete-stream

ストリームの削除

aws kinesis delete-stream --stream-name Foo