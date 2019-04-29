---
title: HDFS の階層制御の S3 のマウント
titleSuffix: SQL Server big data clusters
description: この記事では、HDFS の HDFS に SQL Server 2019 ビッグ データ クラスター (プレビュー) で外部の S3 ファイル システムをマウントする階層化を構成する方法について説明します。
author: nelgson
ms.author: negust
ms.reviewer: jroth
manager: craigg
ms.date: 04/15/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: cd4a5fc600a937b5cc29ea4356a7cc2eb14966b2
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63317121"
---
# <a name="how-to-mount-s3-for-hdfs-tiering-in-a-big-data-cluster"></a>HDFS のビッグ データ クラスター内の階層制御の S3 をマウントする方法

次のセクションでは、HDFS、S3 ストレージのデータ ソースに階層化を構成する方法の例を提供します。

## <a name="prerequisites"></a>前提条件

- [デプロイされたビッグ データ クラスター](deployment-guidance.md)
- [ビッグ データ ツール](deploy-big-data-tools.md)
  - **mssqlctl**
  - **kubectl**
- 作成し、S3 バケットにデータをアップロード 
  - CSV のアップロードまたは Parquet ファイルには、S3 バケット。 これは、ビッグ データ クラスターの HDFS にマウントされる外部 HDFS データです。

## <a name="access-keys"></a>アクセス キー

1. ビッグ データ クラスターにアクセスできるクライアント コンピューターでコマンド プロンプトを開きます。

1. という名前のローカル ファイルを作成する**filename.creds**次の形式を使用して、S3 アカウントの資格情報を格納します。

   ```text
    fs.s3a.access.key=<Access Key ID of the key>
    fs.s3a.secret.key=<Secret Access Key of the key>
   ```

   > [!TIP]
   > S3 を作成する方法の詳細については、アクセス キー (`<s3-access-key>`) を参照してください[S3 のアクセス キー](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys)します。

## <a id="mount"></a> リモートの HDFS の記憶域をマウントします。

資格情報ファイルを用意して、アクセス キーである、マウントを開始します。 次の手順では、S3 で、ビッグ データ クラスターのローカルの HDFS ストレージへのリモートの HDFS storage をマウントできます。

1. 使用**kubectl**の IP アドレスを検索する、 **svc 外部の mgmtproxy**ビッグ データ クラスター サービス。 探して、 **EXTERNAL-IP**します。

   ```bash
   kubectl get svc mgmtproxy-svc-external -n <your-cluster-name>
   ```

1. ログイン**mssqlctl**管理プロキシのエンドポイントの外部 IP アドレスを使用して、クラスター ユーザー名とパスワード。

   ```bash
   mssqlctl login -e https://<IP-of-mgmtproxy-svc-external>:30777/ -u <username> -p <password>
   ```

1. 使用して Azure でリモートの HDFS の記憶域をマウント**mssqlctl ストレージ マウント作成**です。 次のコマンドを実行する前に、プレース ホルダーの値に置き換えます。

   ```bash
   mssqlctl storage mount create --remote-uri s3a://<S3 bucket name> --mount-path /mounts/<mount-name> --credential-file <path-to-s3-credentials>/file.creds
   ```

   > [!NOTE]
   > コマンドの作成、マウントは非同期です。 この時点では、マウントが成功したかどうかを示すメッセージはありません。 参照してください、[状態](#status)セクション、マウントの状態を確認します。

正常にマウントされている場合、HDFS データを照会し、それに対して Spark ジョブを実行できる必要があります。 指定された場所でビッグ データ クラスターの HDFS に表示される`--mount-path`します。

## <a id="status"></a> マウントの状態を取得します。

ビッグ データ クラスター内のすべてのマウントの状態を一覧表示するには、次のコマンドを使用します。

```bash
mssqlctl storage mount status
```

HDFS 内の特定のパスでのマウントの状態を一覧表示するには、次のコマンドを使用します。

```bash
mssqlctl storage mount status --mount-path <mount-path-in-hdfs>
```

## <a id="delete"></a> マウントを削除します。

マウントを削除するには、使用、 **mssqlctl ストレージ マウント delete**コマンド、および HDFS のマウント パスを指定します。

```bash
mssqlctl storage mount delete --mount-path <mount-path-in-hdfs>
```

## <a name="next-steps"></a>次のステップ

SQL Server 2019 ビッグ データ クラスターに関する詳細については、次を参照してください。 [SQL Server 2019 ビッグ データ クラスターには何でしょうか。](big-data-cluster-overview.md)。
