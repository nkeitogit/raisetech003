# 第12回課題提出

## 課題内容

- 提供されたCircleCI のサンプルコンフィグを使用して、正しく動作するようにリポジトリに組み込む

## 準備

- Circleciの登録
- githubとcircleciの連携
- Circleci CLIの導入（Windows）
- Circleci CLI動作確認
- サンプルコンフィグ書き換え


## テスト結果（失敗）

- テストしたファイル（Network.yml）
- テストに使ったブランチ（test）
  
![.circleci](img12/error.png)


### errorの内容

- AZがハードコードされている為、テンプレートの柔軟性が低下しているためバットプラクティス

### errorの解決

- 疑似パラメータ参照・組み込み関数の使用

```yaml
 subnetPublic1a:
    Type: AWS::EC2::Subnet
    Properties:
      AvailabilityZone: !Select
        - 0
        - Fn::GetAZ: !Ref AWS::Region

```

### テスト結果（成功）

![circleci](img12/ok.png)