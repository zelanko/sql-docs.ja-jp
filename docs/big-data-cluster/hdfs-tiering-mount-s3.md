---
title: HDFS の階層制御の S3 のマウント
titleSuffix: SQL Server big data clusters
description: この記事では、SQL Server 2019 ビッグデータクラスター (プレビュー) 上の HDFS に外部 S3 ファイルシステムをマウントするように HDFS 階層を構成する方法について説明します。
author: nelgson
ms.author: negust
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 28c80d6076f07c8a4f1605149f4b5c730c8349a1
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419337"
---
# <a name="how-to-mount-s3-for-hdfs-tiering-in-a-big-data-cluster"></a>ビッグデータクラスターで HDFS 階層化に S3 をマウントする方法

次のセクションでは、S3 ストレージデータソースで HDFS 階層を構成する方法の例について説明します。

## <a name="prerequisites"></a>必須コンポーネント

- [デプロイされたビッグデータクラスター](deployment-guidance.md)
- [ビッグデータツール](deploy-big-data-tools.md)
  - **azdata**
  - **kubectl**
- S3 バケットにデータを作成してアップロードする 
  - CSV または Parquet ファイルを S3 バケットにアップロードします。 これは、ビッグデータクラスターの HDFS にマウントされる外部 HDFS データです。

## <a name="access-keys"></a>アクセス キー

### <a name="set-environment-variable-for-access-key-credentials"></a>アクセスキー資格情報の環境変数を設定する

ビッグデータクラスターにアクセスできるクライアントコンピューターでコマンドプロンプトを開きます。 次の形式を使用して環境変数を設定します。 資格情報はコンマ区切りのリストに含まれている必要があることに注意してください。 Windows では ' set ' コマンドが使用されています。 Linux を使用している場合は、代わりに ' export ' を使用してください。

   ```text
    set MOUNT_CREDENTIALS=fs.s3a.access.key=<Access Key ID of the key>,
    fs.s3a.secret.key=<Secret Access Key of the key>
   ```

   > [!TIP]
   > S3 アクセスキーを作成する方法の詳細については、「 [s3 アクセスキー](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys)」を参照してください。

## <a id="mount"></a>リモート HDFS ストレージをマウントする

アクセスキーを使用して資格情報ファイルを準備したので、マウントを開始できます。 次の手順では、リモート HDFS ストレージを S3 にマウントして、ビッグデータクラスターのローカルの HDFS ストレージに格納します。

1. **Kubectl**を使用して、ビッグデータクラスター内のエンドポイント**コントローラー-svc-外部**サービスの IP アドレスを検索します。 **外部 IP**を探します。

   ```bash
   kubectl get svc controller-svc-external -n <your-big-data-cluster-name>
   ```

1. クラスターのユーザー名とパスワードを使用して、コントローラーエンドポイントの外部 IP アドレスを使用して**azdata**でログインします。

   ```bash
   azdata login -e https://<IP-of-controller-svc-external>:30080/
   ```
   
1. 上記の手順に従って、環境変数 MOUNT_CREDENTIALS を設定します。

1. **Azdata bdc ストレージプールマウント作成**を使用して、Azure にリモート HDFS ストレージをマウントします。 次のコマンドを実行する前に、プレースホルダーの値を置き換えます。

   ```bash
   azdata bdc storage-pool mount create --remote-uri s3a://<S3 bucket name> --mount-path /mounts/<mount-name>
   ```

   > [!NOTE]
   > Mount create コマンドは非同期です。 現時点では、マウントが成功したかどうかを示すメッセージはありません。 マウントの状態を確認するには、[[状態](#status)] セクションを参照してください。

正常にマウントされていれば、HDFS データに対してクエリを実行し、そのデータに対して Spark ジョブを実行できます。 これは、によって`--mount-path`指定された場所にあるビッグデータクラスターの HDFS に表示されます。

## <a id="status"></a>マウントの状態を取得する

ビッグデータクラスター内のすべてのマウントの状態を一覧表示するには、次のコマンドを使用します。

```bash
azdata bdc storage-pool mount status
```

HDFS の特定のパスにあるマウントの状態を一覧表示するには、次のコマンドを使用します。

```bash
azdata bdc storage-pool mount status --mount-path <mount-path-in-hdfs>
```

## <a name="refresh-a-mount"></a>マウントを更新する

次の例では、マウントを更新します。

```bash
azdata bdc hdfs mount refresh --mount-path <mount-path-in-hdfs>
```

## <a id="delete"></a>マウントの削除

マウントを削除するには、 **azdata bdc ストレージプールのマウント削除**コマンドを使用し、HDFS でマウントパスを指定します。

```bash
azdata bdc storage-pool mount delete --mount-path <mount-path-in-hdfs>
```

## <a name="next-steps"></a>次の手順

SQL Server 2019 ビッグ データ クラスターに関する詳細については、次を参照してください。 [SQL Server 2019 ビッグ データ クラスターには何でしょうか](big-data-cluster-overview.md)。
