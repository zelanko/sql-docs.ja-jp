---
title: HDFS の階層制御を構成します。
titleSuffix: SQL Server big data clusters
description: この記事では、HDFS の HDFS に SQL Server 2019 ビッグ データ クラスター (プレビュー) で外部の Azure Data Lake Storage ファイル システムをマウントする階層化を構成する方法について説明します。
author: nelgson
ms.author: negust
ms.reviewer: jroth
manager: craigg
ms.date: 03/27/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 2542c7c05b222517ae9f4a4c05152f21a5ba293b
ms.sourcegitcommit: 2de5446fbc57787f18a907dd5deb02a7831ec07d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58859644"
---
# <a name="configure-hdfs-tiering-on-sql-server-big-data-clusters"></a>HDFS のビッグ データの SQL Server クラスター上の階層制御の構成します。

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

HDFS の階層制御では、HDFS ファイル システムの HDFS と互換性のある、外部にマウントする機能を提供します。 この記事では、HDFS の SQL Server 2019 ビッグ データ クラスター (プレビュー) の階層化を構成する方法について説明します。 この時点で、この記事の焦点である Azure Data Lake ストレージ Gen2 への接続を CTP 2.4 はのみサポートします。

## <a name="hdfs-tiering-overview"></a>HDFS の階層化の概要

階層化、アプリケーションのシームレスなアクセスさまざまな外部ストアでデータ HDFS にデータが存在する場合と同様。 マウントは、メタデータの操作では、HDFS に経由で外部のファイル システム上の名前空間を表すメタデータがコピーされる場所。 このメタデータには、外部のディレクトリとそのアクセス許可や Acl と共にファイルに関する情報が含まれます。 対応するデータは、データ自体にアクセスする場合にのみコピーした、オンデマンドでです。 外部のファイル システムのデータは、SQL Server のビッグ データ クラスターから今すぐアクセスできます。 行うことができます Spark ジョブと SQL クエリでこのデータ クラスター上の HDFS に格納されているすべてのローカル データで実行するのと同様にします。

> [!NOTE]
> Microsoft が開発した機能は、HDFS が階層化し、以前のバージョンには、Apache Hadoop 3.1 ディストリビューションの一部としてリリースされています。 詳細については、次を参照してください。 [ https://issues.apache.org/jira/browse/HDFS-9806 ](https://issues.apache.org/jira/browse/HDFS-9806)詳細についてはします。

次のセクションでは、HDFS、Azure Data Lake ストレージ Gen2 データ ソースと階層化を構成する方法の例を提供します。

## <a name="prerequisites"></a>前提条件

- [デプロイされたビッグ データ クラスター](deployment-guidance.md)
- [ビッグ データ ツール](deploy-big-data-tools.md)
  - **mssqlctl**
  - **kubectl**

## <a id="load"></a> Azure Data Lake Storage にデータを読み込む

次のセクションでは、HDFS が階層化をテストするために Azure Data Lake ストレージ Gen2 を設定する方法について説明します。 Azure Data Lake Storage に格納されたデータが既にあるを場合は、独自のデータを使用するには、このセクションをスキップできます。

1. [Data Lake ストレージ Gen2 機能を備えたストレージ アカウントの作成](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-quickstart-create-account)です。

1. [Blob コンテナーを作成する](https://docs.microsoft.com/azure/storage/blobs/storage-quickstart-blobs-portal)外部データの場合は、このストレージ アカウントにします。

1. CSV、または Parquet ファイルをコンテナーにアップロードします。 これは、ビッグ データ クラスターの HDFS にマウントされる外部 HDFS データです。

## <a id="mount"></a> リモートの HDFS の記憶域をマウントします。

次の手順では、リモートの HDFS のストレージが Azure Data lake、ビッグ データ クラスターの HDFS のローカル ストレージをマウントします。

1. ビッグ データ クラスターにアクセスできるクライアント コンピューターでコマンド プロンプトを開きます。

1. という名前のローカル ファイルを作成する**files.creds**次の形式を使用して、Azure Data Lake ストレージ Gen2 アカウントの資格情報を格納します。

   ```text
   fs.azure.abfs.account.name=<your-storage-account-name>.dfs.core.windows.net
   fs.azure.account.key.<your-storage-account-name>.dfs.core.windows.net=<storage-account-access-key>
   ```

   > [!TIP]
   > アクセス キーを検索する方法の詳細についての (`<storage-account-access-key>`)、ストレージ アカウントを参照してください。[アクセス キーの表示とコピー](https://docs.microsoft.com/azure/storage/common/storage-account-manage?#view-and-copy-access-keys)します。

1. 使用**kubectl**の IP アドレスを検索する、**エンドポイント サービスのプロキシ**ビッグ データ クラスター サービス。 探して、 **EXTERNAL-IP**します。

   ```bash
   kubectl get svc endpoint-service-proxy -n <your-cluster-name>
   ```

1. ログイン**mssqlctl**サービス プロキシのエンドポイントを使用して、クラスター ユーザー名とパスワード。

   ```bash
   mssqlctl login -e https://<IP-of-endpoint-service-proxy>:30777/ -u <username> -p <password>
   ```

1. 使用して Azure でリモートの HDFS の記憶域をマウント**mssqlctl ストレージ マウント作成**です。 次のコマンドを実行する前に、プレース ホルダーの値に置き換えます。

   ```bash
   mssqlctl storage mount create --remote-uri abfs://<blob-container-name>@<storage-account-name>.dfs.core.windows.net/ --mount-path /mounts/<mount-name> --credential-file <path-to-adls-credentials>/file.creds
   ```

   > [!NOTE]
   > コマンドの作成、マウントは非同期です。 この時点では、マウントが成功したかどうかを示すメッセージはありません。 参照してください、[状態](#status)セクション、マウントの状態を確認します。

正常にマウントされている場合、HDFS データを照会し、それに対して Spark ジョブを実行できる必要があります。 指定された場所でビッグ データ クラスターの HDFS に表示される`--local-path`します。

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

## <a id="issues"></a> 既知の問題と制限事項

次の一覧は、HDFS のビッグ データの SQL Server クラスターでの階層化を使用する場合、既知の問題と現在の制限事項を提供します。

- マウントされている外部のディレクトリのサイズが、クラスターの容量よりも大きい場合は、マウントは失敗します。

- マウントがスタックしている場合、`CREATING`がほとんどの場合に失敗した時間が長く状態します。 このような状況では、コマンドをキャンセルし、必要な場合に、マウントを削除します。 パラメーターと資格情報が正しいことを再試行する前に確認します。

- 既存のディレクトリには、マウントを作成することはできません。

- 既存のマウントのマウントを作成できません。

- マウント ポイントの先祖のいずれかが存在しない場合、アクセス許可で作成されますが既定値に r xr xr-x (555)。

- マウントの作成は、マウントされているファイルのサイズと数に応じて時間がかかることができます。 このプロセス中にマウント下のファイルは、ユーザーには表示されません。 マウントの作成中にすべてのファイルは、既定値は、一時的なパスに追加されます`/_temporary/_mounts/<mount-location>`します。

- マウントの作成コマンドは非同期です。 コマンドを実行するは、マウントの状態を把握するマウント状態を確認することができます。

- マウントを作成するときに、引数の使用 **--ローカル パス**マウントの本質的に一意の識別子。 後続のコマンドでは、(、「/」最終的に存在する場合を含む) と同じ文字列を使用する必要があります。

- マウントとは、読み取り専用です。 ディレクトリまたはマウントを下にあるファイルを作成することはできません。

- マウント ディレクトリとファイルを変更することをお勧めしません。 マウントを作成すると後の変更やリモートの場所に更新は、HDFS のマウントに反映するはされません。 リモートの場所に変更が発生した場合は、削除および更新後の状態を反映するように、マウントを再作成できます。

## <a name="next-steps"></a>次のステップ

SQL Server 2019 ビッグ データ クラスターに関する詳細については、次を参照してください。 [SQL Server 2019 ビッグ データ クラスターには何でしょうか。](big-data-cluster-overview.md)。
