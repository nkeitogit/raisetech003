# 第１０回
## 次回までの課題
<br>
1.CloudFormation を利用して、現在までに作った環境をコード化

<br>

2.コード化ができたら実行, 環境が自動で作られることを確認

<br>
<br>




### 作成したtemplate

各レイヤーごとに分けて作成

* <参考>　[AWS black belt](https://www.slideshare.net/AmazonWebServicesJapan/20200826-aws-black-belt-online-seminar-aws-cloudformation-238501102)
  
* * *

### Network Layer

* [VPC](cloudfomation/net/NET.yml)
  
* * *



### securitygroup Layer

* [securitygroup](cloudfomation/security/securitygroupLayer.yml)
* [IAM](cloudfomation/security/Iam.yml)

* * *


### application Layer

* [ALB](cloudfomation/app/ALB.yml)
* [EC2](cloudfomation/app/EC2.yml)
* [RDS](cloudfomation/app/RDS.yml)
* [S3](cloudfomation/app/S3.yml)


* * * 

### スタックの証跡


![sutakku](img10/suttke.png)

* * *
### やったこと


* AWS　consoleで作成してみてどんな意味で書いているか、またはどのような記述なのかをtemplateの記述と照らし合わせてみながら作成した
* 公式ドキュメントを参照しながら行った、これは必須か必須じゃないか（一部日本語対応してないものがあって苦戦した）
* VScodeの各種設定
  
### 今後やっていきたいこと

* IaCジェネレーターとFormer２の使用して以前につくったresourceをコード化してみる
* AWS CLIを使っての外部ファイルの参照

