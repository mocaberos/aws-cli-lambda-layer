# aws-cli-lambda-layer
AWS Lambda上で aws-cliコマンドを使用するためのレイヤー

## 使い方
下記のコマンドを使用するとaws-cliという名前でLambdaレイヤーがデプロイされます。
python3のランタイムを使用したLambda関数に付けると、Lambda関数からaws-cliを使用することができます。
```shell
$ git clone https://github.com/mocaberos/aws-cli-lambda-layer.git

$ cd aws-cli-lambda-layer

$ zip -r aws-cli-layer.zip ./lambda-layer

$ aws lambda publish-layer-version --layer-name aws-cli --description "for aws cli" --zip-file fileb://aws-cli-layer.zip --compatible-runtimes python3.6 python3.7 python3.8 python3.9
```
Lambda関数内でaws-cliを呼び出す方法
```python
# `/opt/aws`に配置されます。
import subprocess
subprocess.call('/opt/aws --version', shell=True)
```

## レイヤーの生成
python3がインストールされた環境で`setup`スクリプトを実行すると、`lambda-layer`ディレクトリが生成されます。
