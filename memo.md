# めも

## zappaの起動

python3.9だと実行できなかったので3.8以下（自分のZappaのバージョンだと3.6,3.7,3.8が使えた）

## Scheduledのエラー

> AttributeError: 'Template' object has no attribute 'add_description'

こんなエラーがでた  
以下のパッケージをインストールして解決  

```shell
pip install troposphere==2.7.1
```

## CloudFormationのエラー

> botocore.exceptions.ParamValidationError: Parameter validation failed:
> Invalid type for parameter restApiId, value: None, type: <class 'NoneType'>, valid types: <class 'str'>

こんなエラーがでた  
見たところ↓のエラーも出てたのでCloudFormationで手動でStackを作成（テンプレートはローカルに作成されたJSONファイルを仕様）して対応

```shell
Stack 'serverless-pyth-dev' does not exist
```

## APIGatewayのエラー

> Error: Warning! Status check on the deployed lambda failed. A GET request to '/' yielded a 502 response code.

こんなエラーがでた  
どうやらZappaCLI使ってる時に起動ファイルの設定でスペルミスがあった模様

## DynamoDBローカルの立ち上げ方

dynamodb_local_latestフォルダに移動してから実行

```shell
$ java "-Djava.library.path=./DynamoDBLocal_lib" -jar DynamoDBLocal.jar -sharedDb
```