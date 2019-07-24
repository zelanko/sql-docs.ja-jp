---
title: HDFS 階層を構成する
titleSuffix: SQL Server big data clusters
description: この記事では、SQL Server 2019 ビッグデータクラスター (プレビュー) 上の HDFS に外部 Azure Data Lake Storage ファイルシステムをマウントするように HDFS 階層を構成する方法について説明します。
author: nelgson
ms.author: negust
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 17eedf9f0797a0adb5eda6ca8ee090fc762e1491
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419380"
---
# <a name="configure-hdfs-tiering-on-sql-server-big-data-clusters"></a>ビッグデータクラスター SQL Server で HDFS 階層を構成する

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Hdfs 階層化は、hdfs に外部の HDFS と互換性のあるファイルシステムをマウントする機能を提供します。 この記事では、SQL Server 2019 ビッグデータクラスター (プレビュー) の HDFS 階層を構成する方法について説明します。 現時点では、Azure Data Lake Storage Gen2 および Amazon S3 への接続がサポートされています。 

## <a name="hdfs-tiering-overview"></a>HDFS 階層化の概要

階層化により、アプリケーションは、データがローカルの HDFS に存在する場合と同様に、さまざまな外部ストアのデータにシームレスにアクセスできます。 マウントはメタデータ操作であり、外部ファイルシステムの名前空間を記述するメタデータがローカルの HDFS にコピーされます。 このメタデータには、外部ディレクトリおよびファイルに関する情報と、そのアクセス許可と Acl が含まれます。 クエリなどを通じてデータ自体にアクセスする場合、対応するデータは要求時にのみコピーされます。 これで、SQL Server ビッグデータクラスターから外部ファイルシステムデータにアクセスできるようになりました。 このデータに対して Spark ジョブと SQL クエリを実行する方法は、クラスター上の HDFS に格納されているローカルデータに対して実行する方法と同じです。

### <a name="caching"></a>キャッシュ
現在、既定では、合計 HDFS ストレージの 1% が、マウントされたデータのキャッシュ用に予約されます。 キャッシュは、マウント全体でグローバルに設定されます。

> [!NOTE]
> HDFS の階層化は、Microsoft によって開発された機能であり、Apache Hadoop 3.1 ディストリビューションの一部としてリリースされています。 詳細については[https://issues.apache.org/jira/browse/HDFS-9806](https://issues.apache.org/jira/browse/HDFS-9806) 、「」を参照してください。

次のセクションでは、Azure Data Lake Storage Gen2 データソースで HDFS 階層を構成する方法の例について説明します。

## <a name="refresh"></a>Refresh

HDFS の階層化は更新をサポートします。 既存のマウントを更新して、リモートデータの最新のスナップショットを入手します。

## <a name="prerequisites"></a>必須コンポーネント

- [デプロイされたビッグデータクラスター](deployment-guidance.md)
- [ビッグデータツール](deploy-big-data-tools.md)
  - **azdata**
  - **kubectl**

## <a name="mounting-instructions"></a>マウントの手順

Azure Data Lake Storage Gen2 と Amazon S3 への接続がサポートされています。 これらのストレージの種類に対してマウントする方法については、次の記事を参照してください。

- [ビッグデータクラスターで HDFS 階層化 ADLS Gen2 をマウントする方法](hdfs-tiering-mount-adlsgen2.md)
- [ビッグデータクラスターで HDFS 階層化に S3 をマウントする方法](hdfs-tiering-mount-s3.md)

## <a id="issues"></a>既知の問題と制限事項

次の一覧に、SQL Server ビッグデータクラスターで HDFS 階層化を使用する場合の既知の問題と現在の制限事項を示します。

- マウントが`CREATING`長時間停止している場合は、失敗する可能性が最も高くなります。 このような場合は、コマンドを取り消し、必要に応じてマウントを削除します。 再試行する前に、パラメーターと資格情報が正しいことを確認してください。

- 既存のディレクトリにマウントを作成することはできません。

- 既存のマウント内にマウントを作成することはできません。

- マウントポイントのいずれかの先祖が存在しない場合は、xr-xr-x (555) を既定とするアクセス許可を使用して作成されます。

- マウントされるファイルの数とサイズによっては、マウントの作成に時間がかかることがあります。 この処理中に、マウントされたファイルはユーザーに表示されません。 マウントが作成されると、すべてのファイルが一時パスに追加され`/_temporary/_mounts/<mount-location>`ます。既定値はです。

- マウント作成コマンドは非同期です。 コマンドが実行された後、マウントの状態を確認して、マウントの状態を把握できます。

- マウントを作成する場合、 **--mount-path**に使用される引数は、基本的にマウントの一意の識別子です。 後続のコマンドでは、同じ文字列 (末尾の "/" を含む) を使用する必要があります。

- マウントは読み取り専用です。 マウントの下にディレクトリまたはファイルを作成することはできません。

- 変更できるディレクトリとファイルのマウントはお勧めしません。 マウントが作成されると、リモートの場所に対する変更や更新は、HDFS のマウントに反映されません。 リモートの場所で変更が発生した場合は、更新された状態を反映するようにマウントを削除して再作成することを選択できます。

## <a name="next-steps"></a>次のステップ

SQL Server 2019 ビッグ データ クラスターに関する詳細については、次を参照してください。 [SQL Server 2019 ビッグ データ クラスターには何でしょうか](big-data-cluster-overview.md)。
