---
title: HDFS の階層制御の S3 のマウント
titleSuffix: SQL Server big data clusters
description: この記事では、HDFS の HDFS に SQL Server 2019 ビッグ データ クラスター (プレビュー) で外部の S3 ファイル システムをマウントする階層化を構成する方法について説明します。
author: nelgson
ms.author: negust
ms.reviewer: mikeray
manager: jroth
ms.date: 06/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d782a2c8727f053b569c77af525795d81afebbc7
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67728742"
---
# <a name="how-to-mount-s3-for-hdfs-tiering-in-a-big-data-cluster"></a>HDFS のビッグ データ クラスター内の階層制御の S3 をマウントする方法

次のセクションでは、HDFS、S3 ストレージのデータ ソースに階層化を構成する方法の例を提供します。

## <a name="prerequisites"></a>必須コンポーネント

- [デプロイされたビッグ データ クラスター](deployment-guidance.md)
- [ビッグ データ ツール](deploy-big-data-tools.md)
  - **mssqlctl**
  - **kubectl**
- 作成し、S3 バケットにデータをアップロード 
  - CSV のアップロードまたは Parquet ファイルには、S3 バケット。 これは、ビッグ データ クラスターの HDFS にマウントされる外部 HDFS データです。

## <a name="access-keys"></a>アクセス キー

### <a name="set-environment-variable-for-access-key-credentials"></a>アクセス キーの資格情報の環境変数を設定します。

ビッグ データ クラスターにアクセスできるクライアント コンピューターでコマンド プロンプトを開きます。 次の形式を使用して、環境変数を設定します。 区切りのリストをコンマである必要があります、資格情報に注意してください。 'Set' コマンドは、Windows で使用されます。 Linux を使用している場合は、代わりに 'export' を使用しています。

   ```text
    set MOUNT_CREDENTIALS=fs.s3a.access.key=<Access Key ID of the key>,
    fs.s3a.secret.key=<Secret Access Key of the key>
   ```

   > [!TIP]
   > S3 のアクセス キーを作成する方法の詳細については、次を参照してください。 [S3 のアクセス キー](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys)します。

## <a id="mount"></a> リモートの HDFS の記憶域をマウントします。

資格情報ファイルを用意して、アクセス キーである、マウントを開始します。 次の手順では、S3 で、ビッグ データ クラスターのローカルの HDFS ストレージへのリモートの HDFS storage をマウントできます。

1. 使用**kubectl**エンドポイントの IP アドレスを検索する**svc 外部のコント ローラー**ビッグ データ クラスター サービス。 探して、 **EXTERNAL-IP**します。

   ```bash
   kubectl get svc controller-svc-external -n <your-big-data-cluster-name>
   ```

1. ログイン**mssqlctl**コント ローラーのエンドポイントの外部 IP アドレスを使用して、クラスター ユーザー名とパスワード。

   ```bash
   mssqlctl login -e https://<IP-of-controller-svc-external>:30080/
   ```
   
1. 上記の手順に従ってください MOUNT_CREDENTIALS 環境変数な設定

1. 使用して Azure でリモートの HDFS の記憶域をマウント**mssqlctl bdc 記憶域プールのマウント作成**です。 次のコマンドを実行する前に、プレース ホルダーの値に置き換えます。

   ```bash
   mssqlctl bdc storage-pool mount create --remote-uri s3a://<S3 bucket name> --mount-path /mounts/<mount-name>
   ```

   > [!NOTE]
   > コマンドの作成、マウントは非同期です。 この時点では、マウントが成功したかどうかを示すメッセージはありません。 参照してください、[状態](#status)セクション、マウントの状態を確認します。

正常にマウントされている場合、HDFS データを照会し、それに対して Spark ジョブを実行できる必要があります。 指定された場所でビッグ データ クラスターの HDFS に表示される`--mount-path`します。

## <a id="status"></a> マウントの状態を取得します。

ビッグ データ クラスター内のすべてのマウントの状態を一覧表示するには、次のコマンドを使用します。

```bash
mssqlctl bdc storage-pool mount status
```

HDFS 内の特定のパスでのマウントの状態を一覧表示するには、次のコマンドを使用します。

```bash
mssqlctl bdc storage-pool mount status --mount-path <mount-path-in-hdfs>
```

## <a id="delete"></a> マウントを削除します。

マウントを削除するには使用、 **mssqlctl bdc 記憶域プールのマウント delete**コマンド、および HDFS のマウント パスを指定します。

```bash
mssqlctl bdc storage-pool mount delete --mount-path <mount-path-in-hdfs>
```

## <a name="next-steps"></a>次の手順

SQL Server 2019 ビッグ データ クラスターに関する詳細については、次を参照してください。 [SQL Server 2019 ビッグ データ クラスターには何でしょうか](big-data-cluster-overview.md)。
