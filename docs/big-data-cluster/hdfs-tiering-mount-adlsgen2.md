---
title: HDFS の階層制御の ADLS Gen2 のマウント
titleSuffix: How to mount ADLS Gen2
description: この記事では、HDFS の HDFS に SQL Server 2019 ビッグ データ クラスター (プレビュー) で外部の Azure Data Lake Storage ファイル システムをマウントする階層化を構成する方法について説明します。
author: nelgson
ms.author: negust
ms.reviewer: mikeray
ms.date: 06/27/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: ce7836b66408fda5f60e5566625dc1aa460fa672
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67958370"
---
# <a name="how-to-mount-adls-gen2-for-hdfs-tiering-in-a-big-data-cluster"></a>マウント ADLS Gen2 の HDFS のビッグ データ クラスター内の階層化する方法

次のセクションでは、HDFS、Azure Data Lake ストレージ Gen2 データ ソースと階層化を構成する方法の例を提供します。

## <a name="prerequisites"></a>必須コンポーネント

- [デプロイされたビッグ データ クラスター](deployment-guidance.md)
- [ビッグ データ ツール](deploy-big-data-tools.md)
  - **mssqlctl**
  - **kubectl**

## <a id="load"></a> Azure Data Lake Storage にデータを読み込む

次のセクションでは、HDFS が階層化をテストするために Azure Data Lake ストレージ Gen2 を設定する方法について説明します。 Azure Data Lake Storage に格納されたデータが既にあるを場合は、独自のデータを使用するには、このセクションをスキップできます。

1. [Data Lake ストレージ Gen2 機能を備えたストレージ アカウントの作成](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-quickstart-create-account)です。

1. [Blob コンテナーを作成する](https://docs.microsoft.com/azure/storage/blobs/storage-quickstart-blobs-portal)外部データの場合は、このストレージ アカウントにします。

1. CSV、または Parquet ファイルをコンテナーにアップロードします。 これは、ビッグ データ クラスターの HDFS にマウントされる外部 HDFS データです。

## <a name="credentials-for-mounting"></a>マウントの資格情報

## <a name="use-oauth-credentials-to-mount"></a>OAuth の資格情報を使用してマウントするには

実行する必要をマウントする OAuth 資格情報を使用するには、次の手順。

1. 移動して、 [Azure portal](https://portal.azure.com)
1. 左側のナビゲーション ウィンドウで"services"に移動し、"Azure Active Directory"クロック
1. "Web アプリケーションと、ウィザードに従って"アプリの登録 を使用して、メニューで、作成します。 **ここで作成した名前を覚えて**します。 権限を持つユーザーとして ADLS アカウントにこの名前を追加する必要があります。
1. Web アプリケーションを作成した後は、アプリの [設定] [キー] に移動します。
1. クリックしてキーの有効期間の保存を選択します。 **生成されたキーを保存します。**
1.  アプリの登録 ページに戻るし、上部にある エンドポイント ボタンをクリックします。 **「トークン エンドポイント」URL をメモします。**
1. OAuth のメモ、次の操作を取得できました。

    - Web アプリの"アプリケーション ID"上記手順で作成した 3
    - 手順 5. で生成したキー
    - 手順 6 からのトークン エンドポイント

### <a name="adding-the-service-principal-to-your-adls-account"></a>サービス プリンシパルを ADLS アカウントに追加します。

1. 、再度ポータルに戻るし、ADLS アカウントを開いて左側のメニューでアクセス制御 (IAM) を選択します。
1. "ロールの割り当ての追加 を選択し、(、一覧には表示されませんがが見つかるかどうかは検索する完全な名前をメモ) 上記の手順 3 で作成した名前を検索します。
1. 「ストレージ Blob データ共同作成者 (プレビュー)」の役割を追加します。

マウントの資格情報を使用する前に 5 ~ 10 分間待機します。

### <a name="set-environment-variable-for-oauth-credentials"></a>OAuth の資格情報の環境変数を設定します。

ビッグ データ クラスターにアクセスできるクライアント コンピューターでコマンド プロンプトを開きます。 次の形式を使用して環境変数を設定します。区切りのリストをコンマである必要があります、資格情報に注意してください。 'Set' コマンドは、Windows で使用されます。 Linux を使用している場合は、代わりに 'export' を使用しています。

   ```text
    set MOUNT_CREDENTIALS=fs.azure.account.auth.type=OAuth,
    fs.azure.account.oauth.provider.type=org.apache.hadoop.fs.azurebfs.oauth2.ClientCredsTokenProvider,
    fs.azure.account.oauth2.client.endpoint=[token endpoint from step6 above],
    fs.azure.account.oauth2.client.id=[<Application ID> from step3 above],
    fs.azure.account.oauth2.client.secret=[<key> from step5 above]
   ```

## <a name="use-access-keys-to-mount"></a>アクセス キーを使用してマウントするには

Azure portal で ADLS アカウントを取得できるアクセス キーの使用をマウントできます。

 > [!TIP]
   > アクセス キーを検索する方法の詳細についての (`<storage-account-access-key>`)、ストレージ アカウントを参照してください。[アカウント キーと接続文字列を表示](/azure/storage/common/storage-account-manage#view-account-keys-and-connection-string)します。

### <a name="set-environment-variable-for-access-key-credentials"></a>アクセス キーの資格情報の環境変数を設定します。

1. ビッグ データ クラスターにアクセスできるクライアント コンピューターでコマンド プロンプトを開きます。

1. ビッグ データ クラスターにアクセスできるクライアント コンピューターでコマンド プロンプトを開きます。 次の形式を使用して、環境変数を設定します。 区切りのリストをコンマである必要があります、資格情報に注意してください。 'Set' コマンドは、Windows で使用されます。 Linux を使用している場合は、代わりに 'export' を使用しています。

   ```text
   set MOUNT_CREDENTIALS=fs.azure.abfs.account.name=<your-storage-account-name>.dfs.core.windows.net,
   fs.azure.account.key.<your-storage-account-name>.dfs.core.windows.net=<storage-account-access-key>
   ```

## <a id="mount"></a> リモートの HDFS の記憶域をマウントします。

アクセス キーまたは OAuth を使用して MOUNT_CREDENTIALS 環境変数を設定すると、マウントを開始します。 次の手順では、ビッグ データ クラスターのローカルの HDFS ストレージに Azure Data Lake でリモートの HDFS ストレージをマウントします。

1. 使用**kubectl**エンドポイントの IP アドレスを検索する**svc 外部のコント ローラー**ビッグ データ クラスター サービス。 探して、 **EXTERNAL-IP**します。

   ```bash
   kubectl get svc controller-svc-external -n <your-big-data-cluster-name>
   ```

1. ログイン**mssqlctl**コント ローラーのエンドポイントの外部 IP アドレスを使用して、クラスター ユーザー名とパスワード。

   ```bash
   mssqlctl login -e https://<IP-of-controller-svc-external>:30080/
   ```
1. 環境変数な設定 MOUNT_CREDENTIALS (スクロール手順用に)

1. 使用して Azure でリモートの HDFS の記憶域をマウント**mssqlctl bdc 記憶域プールのマウント作成**です。 次のコマンドを実行する前に、プレース ホルダーの値に置き換えます。

   ```bash
   mssqlctl bdc storage-pool mount create --remote-uri abfs://<blob-container-name>@<storage-account-name>.dfs.core.windows.net/ --mount-path /mounts/<mount-name>
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
