---
title: HDFS の階層制御の ADLS Gen2 のマウント
titleSuffix: How to mount ADLS Gen2
description: この記事では、SQL Server 2019 ビッグデータクラスター (プレビュー) 上の HDFS に外部 Azure Data Lake Storage ファイルシステムをマウントするように HDFS 階層を構成する方法について説明します。
author: nelgson
ms.author: negust
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d7d8a6dd53452700853dca9774ed0196ed7546fe
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419348"
---
# <a name="how-to-mount-adls-gen2-for-hdfs-tiering-in-a-big-data-cluster"></a>ビッグデータクラスターで HDFS 階層化 ADLS Gen2 をマウントする方法

次のセクションでは、Azure Data Lake Storage Gen2 データソースで HDFS 階層を構成する方法の例について説明します。

## <a name="prerequisites"></a>必須コンポーネント

- [デプロイされたビッグデータクラスター](deployment-guidance.md)
- [ビッグデータツール](deploy-big-data-tools.md)
  - **azdata**
  - **kubectl**

## <a id="load"></a>Azure Data Lake Storage にデータを読み込む

次のセクションでは、HDFS 階層化をテストするための Azure Data Lake Storage Gen2 を設定する方法について説明します。 Azure Data Lake Storage に既にデータが格納されている場合は、このセクションを省略して独自のデータを使用することができます。

1. [Data Lake Storage Gen2 機能を持つストレージアカウントを作成](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-quickstart-create-account)します。

1. このストレージアカウントに外部データ用の[blob コンテナーを作成](https://docs.microsoft.com/azure/storage/blobs/storage-quickstart-blobs-portal)します。

1. CSV ファイルまたは Parquet ファイルをコンテナーにアップロードします。 これは、ビッグデータクラスターの HDFS にマウントされる外部 HDFS データです。

## <a name="credentials-for-mounting"></a>マウント用の資格情報

## <a name="use-oauth-credentials-to-mount"></a>OAuth 資格情報を使用してマウントする

OAuth 資格情報を使用してをマウントするには、次の手順に従う必要があります。

1. [Azure portal](https://portal.azure.com)にアクセス
1. 左側のナビゲーションウィンドウで [サービス] に移動し、[Azure Active Directory]
1. メニューの [アプリの登録] を使用して、"Web アプリケーション" を作成し、ウィザードの指示に従います。 **ここで作成する名前を忘れないで**ください。 この名前を ADLS アカウントに承認されたユーザーとして追加する必要があります。
1. Web アプリケーションが作成されたら、アプリの [設定] の下にある [キー] にアクセスします。
1. キーの期間を選択し、[保存] をクリックします。 **生成されたキーを保存します。**
1.  [アプリの登録] ページに戻り、上部にある [エンドポイント] ボタンをクリックします。 **"トークンエンドポイント" の URL をメモしておきます。**
1. OAuth に関しては、次の点に注意する必要があります。

    - 手順3で作成した Web アプリの "アプリケーション ID"
    - 手順 5. で生成したキー
    - 手順6のトークンエンドポイント

### <a name="adding-the-service-principal-to-your-adls-account"></a>サービスプリンシパルを ADLS アカウントに追加しています

1. ポータルにもう一度移動し、ADLS アカウントを開き、左側のメニューで [アクセス制御 (IAM)] を選択します。
1. [ロールの割り当てを追加] を選択し、上の手順3で作成した名前を検索します (一覧には表示されませんが、完全な名前を検索した場合は検出されます)。
1. ここで、"Storage Blob データ共同作成者 (プレビュー)" ロールを追加します。

マウントに資格情報を使用する前に、5-10 分間待機します。

### <a name="set-environment-variable-for-oauth-credentials"></a>OAuth 資格情報の環境変数を設定する

ビッグデータクラスターにアクセスできるクライアントコンピューターでコマンドプロンプトを開きます。 次の形式を使用して環境変数を設定します。資格情報はコンマ区切りのリストに含まれている必要があることに注意してください。 Windows では ' set ' コマンドが使用されています。 Linux を使用している場合は、代わりに ' export ' を使用してください。

   ```text
    set MOUNT_CREDENTIALS=fs.azure.account.auth.type=OAuth,
    fs.azure.account.oauth.provider.type=org.apache.hadoop.fs.azurebfs.oauth2.ClientCredsTokenProvider,
    fs.azure.account.oauth2.client.endpoint=[token endpoint from step6 above],
    fs.azure.account.oauth2.client.id=[<Application ID> from step3 above],
    fs.azure.account.oauth2.client.secret=[<key> from step5 above]
   ```

## <a name="use-access-keys-to-mount"></a>アクセスキーを使用してマウントする

また、Azure portal で ADLS アカウント用に取得できるアクセスキーを使用してマウントすることもできます。

 > [!TIP]
   > ストレージアカウントのアクセスキー (`<storage-account-access-key>`) を検索する方法の詳細については、「[アカウントキーと接続文字列の表示](/azure/storage/common/storage-account-manage#view-account-keys-and-connection-string)」を参照してください。

### <a name="set-environment-variable-for-access-key-credentials"></a>アクセスキー資格情報の環境変数を設定する

1. ビッグデータクラスターにアクセスできるクライアントコンピューターでコマンドプロンプトを開きます。

1. ビッグデータクラスターにアクセスできるクライアントコンピューターでコマンドプロンプトを開きます。 次の形式を使用して環境変数を設定します。 資格情報はコンマ区切りのリストに含まれている必要があることに注意してください。 Windows では ' set ' コマンドが使用されています。 Linux を使用している場合は、代わりに ' export ' を使用してください。

   ```text
   set MOUNT_CREDENTIALS=fs.azure.abfs.account.name=<your-storage-account-name>.dfs.core.windows.net,
   fs.azure.account.key.<your-storage-account-name>.dfs.core.windows.net=<storage-account-access-key>
   ```

## <a id="mount"></a>リモート HDFS ストレージをマウントする

アクセスキーまたは OAuth を使用するように MOUNT_CREDENTIALS 環境変数を設定したので、マウントを開始できます。 次の手順では、Azure Data Lake のリモート HDFS ストレージを、ビッグデータクラスターのローカルの HDFS ストレージにマウントします。

1. **Kubectl**を使用して、ビッグデータクラスター内のエンドポイント**コントローラー-svc-外部**サービスの IP アドレスを検索します。 **外部 IP**を探します。

   ```bash
   kubectl get svc controller-svc-external -n <your-big-data-cluster-name>
   ```

1. クラスターのユーザー名とパスワードを使用して、コントローラーエンドポイントの外部 IP アドレスを使用して**azdata**でログインします。

   ```bash
   azdata login -e https://<IP-of-controller-svc-external>:30080/
   ```
1. 環境変数 MOUNT_CREDENTIALS の設定 (手順については上へスクロール)

1. **Azdata bdc ストレージプールマウント作成**を使用して、Azure にリモート HDFS ストレージをマウントします。 次のコマンドを実行する前に、プレースホルダーの値を置き換えます。

   ```bash
   azdata bdc storage-pool mount create --remote-uri abfs://<blob-container-name>@<storage-account-name>.dfs.core.windows.net/ --mount-path /mounts/<mount-name>
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
