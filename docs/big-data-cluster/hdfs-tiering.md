---
title: HDFS の階層制御を構成します。
titleSuffix: SQL Server big data clusters
description: この記事では、HDFS の HDFS に SQL Server 2019 ビッグ データ クラスター (プレビュー) で外部の Azure Data Lake Storage ファイル システムをマウントする階層化を構成する方法について説明します。
author: nelgson
ms.author: negust
ms.reviewer: jroth
manager: jroth
ms.date: 04/23/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: a36bd28efd128a76246297995d712b417d7f230d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66782104"
---
# <a name="configure-hdfs-tiering-on-sql-server-big-data-clusters"></a>HDFS のビッグ データの SQL Server クラスター上の階層制御の構成します。

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

HDFS の階層制御では、HDFS ファイル システムの HDFS と互換性のある、外部にマウントする機能を提供します。 この記事では、HDFS の SQL Server 2019 ビッグ データ クラスター (プレビュー) の階層化を構成する方法について説明します。 現時点では、Azure Data Lake ストレージの Gen2 および Amazon S3 への接続をサポートします。 

## <a name="hdfs-tiering-overview"></a>HDFS の階層化の概要

階層化、アプリケーションのシームレスなアクセスさまざまな外部ストアでデータ、ローカルの HDFS にデータが存在する場合と同様。 マウントは、メタデータの操作をローカルの HDFS に経由で外部のファイル システム上の名前空間を表すメタデータがコピーされる場所。 このメタデータには、外部のディレクトリとそのアクセス許可や Acl と共にファイルに関する情報が含まれます。 対応するデータは、たとえば、クエリ、データ自体にアクセスする場合にのみコピーした、オンデマンドでです。 外部のファイル システムのデータは、SQL Server のビッグ データ クラスターから今すぐアクセスできます。 行うことができます Spark ジョブと SQL クエリでこのデータ クラスター上の HDFS に格納されているすべてのローカル データで実行するのと同様にします。

### <a name="caching"></a>キャッシュ
今日では、既定では、HDFS ストレージの合計の 1% が予約されますマウントされたデータのキャッシュ。 キャッシュは、グローバル設定を使って、マウント全体です。

> [!NOTE]
> Microsoft が開発した機能は、HDFS が階層化し、以前のバージョンには、Apache Hadoop 3.1 ディストリビューションの一部としてリリースされています。 詳細については、次を参照してください。 [ https://issues.apache.org/jira/browse/HDFS-9806 ](https://issues.apache.org/jira/browse/HDFS-9806)詳細についてはします。

次のセクションでは、HDFS、Azure Data Lake ストレージ Gen2 データ ソースと階層化を構成する方法の例を提供します。

## <a name="prerequisites"></a>前提条件

- [デプロイされたビッグ データ クラスター](deployment-guidance.md)
- [ビッグ データ ツール](deploy-big-data-tools.md)
  - **mssqlctl**
  - **kubectl**

## <a name="mounting-instructions"></a>マウント操作手順

Azure Data Lake ストレージ Gen2 および Amazon S3 への接続がサポートされます。 これらの記憶域の種類に対してをマウントする方法については、次の記事を参照してください。

- [マウント ADLS Gen2 の HDFS のビッグ データ クラスター内の階層化する方法](hdfs-tiering-mount-adlsgen2.md)
- [HDFS のビッグ データ クラスター内の階層制御の S3 をマウントする方法](hdfs-tiering-mount-s3.md)

## <a id="issues"></a> 既知の問題と制限事項

次の一覧は、HDFS のビッグ データの SQL Server クラスターでの階層化を使用する場合、既知の問題と現在の制限事項を提供します。

- マウントがスタックしている場合、`CREATING`がほとんどの場合に失敗した時間が長く状態します。 このような状況では、コマンドをキャンセルし、必要な場合に、マウントを削除します。 パラメーターと資格情報が正しいことを再試行する前に確認します。

- 既存のディレクトリには、マウントを作成することはできません。

- 既存のマウントのマウントを作成できません。

- マウント ポイントの先祖のいずれかが存在しない場合、アクセス許可で作成されますが既定値に r xr xr-x (555)。

- マウントの作成は、マウントされているファイルのサイズと数に応じて時間がかかることができます。 このプロセス中にマウント下のファイルは、ユーザーには表示されません。 マウントの作成中にすべてのファイルは、既定値は、一時的なパスに追加されます`/_temporary/_mounts/<mount-location>`します。

- マウントの作成コマンドは非同期です。 コマンドを実行するは、マウントの状態を把握するマウント状態を確認することができます。

- マウントを作成するときに、引数の使用 **--マウント パス**マウントの本質的に一意の識別子。 後続のコマンドでは、(、「/」最終的に存在する場合を含む) と同じ文字列を使用する必要があります。

- マウントとは、読み取り専用です。 ディレクトリまたはマウントを下にあるファイルを作成することはできません。

- マウント ディレクトリとファイルを変更することをお勧めしません。 マウントを作成すると後の変更やリモートの場所に更新は、HDFS のマウントに反映するはされません。 リモートの場所に変更が発生した場合は、削除および更新後の状態を反映するように、マウントを再作成できます。

## <a name="next-steps"></a>次のステップ

SQL Server 2019 ビッグ データ クラスターに関する詳細については、次を参照してください。 [SQL Server 2019 ビッグ データ クラスターには何でしょうか](big-data-cluster-overview.md)。
