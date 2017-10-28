---
title: "インストールと構成 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- samples
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6dd1f09b-dcff-4627-899a-eca5162d9e5b
caps.latest.revision: 4
author: BarbKess
ms.author: barbkess
manager: jhubbard
robots: noindex,nofollow
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: 3b4a02b7b8c17f6bd5a75714a8fc3357dcfbd9a3
ms.contentlocale: ja-jp
ms.lasthandoff: 09/27/2017

---
# <a name="installation-and-configuration"></a>インストールと構成
Wide World importers 社の OLTP データベースのインストールと構成手順です。

## <a name="prerequisites"></a>前提条件

- [SQL Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016) (またはそれ以降) または[Azure SQL Database](https://azure.microsoft.com/services/sql-database/)です。 完全バージョンのサンプルでは、SQL Server Evaluation/Developer または Enterprise Edition を使用します。
- [SQL Server Management Studio](../../ssms/download-sql-server-management-studio-ssms.md)。 最良の結果は、2016 年 6 月リリースを使用またはそれ以降。

## <a name="download"></a>ダウンロード

サンプルの最新リリース。

[wide world importers 社リリース](http://go.microsoft.com/fwlink/?LinkID=800630)

SQL Server または Azure SQL データベースのエディションにサンプル WideWorldImporters データベースのバックアップ/bacpac には、対応するをダウンロードします。

サンプル データベースを再作成するソース コードは、次の場所から使用可能なです。 このサンプルを再作成する原因になるデータ、わずかに異なるデータ生成時に、ランダムな要素があるので注意してください。

[wide world-importers 社](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers/wwi-database-scripts)

## <a name="install"></a>Install


### <a name="sql-server"></a>SQL Server

SQL Server インスタンスにバックアップを復元するには、Management Studio を使用できます。

1. SQL Server Management Studio を開き、対象の SQL Server インスタンスに接続します。
2. 右クリックし、**データベース**ノード、および選択**Restore Database**です。
3. 選択**デバイス**、ボタンをクリック**しています.**
4. ダイアログ ボックスで**バックアップ デバイスの選択**、 をクリックして**追加**データベースのバックアップをサーバーのファイル システムに移動し、バックアップを選択します。 **[OK]**をクリックします。
5. 必要な場合は、データのターゲットの場所を変更し、で、ログ ファイル、**ファイル**ウィンドウです。 ベスト プラクティスにデータを配置し、ログ ファイルを別のドライブにあることに注意してください。
6. **[OK]**をクリックします。 データベースの復元が開始されます。 それが完了した後、データベース、SQL Server インスタンスにインストールされている WideWorldImporters があります。

### <a name="azure-sql-database"></a>Azure SQL データベース

新しい SQL データベースに bacpac をインポートするには、Management Studio を使用できます。

1. (省略可能)Azure で SQL Server がいない場合に移動、 [Azure ポータル](https://portal.azure.com/)し、新しい SQL データベースを作成します。 途中でデータベースを作成、サーバーを作成します。 サーバーのメモしてをおきます。
   - 参照してください[このチュートリアル](https://azure.microsoft.com/documentation/articles/sql-database-get-started/)分単位でデータベースを作成するには
2. SQL Server Management Studio を開き、Azure 内のサーバーに接続します。
3. 右クリックし、**データベース**ノード、および選択**データ層アプリケーションのインポート**です。
4. **設定のインポート**選択**ローカル ディスクからインポート**し、ファイル システムから、サンプル データベースの bacpac を選択します。
5. **データベース設定**するデータベースの名前を変更*WideWorldImporters*しを使用するターゲットのエディションやサービスの目標を選択します。
6. をクリックして**[次へ]**と**完了**展開を開始します。 P1 を完了するまで数分が行われます。 低い料金する場合は、階層が必要に応じて、P1 の新しいデータベースにインポートし、目的のレベルには価格レベルを変更することをお勧めします。

## <a name="configuration"></a>構成

### <a name="full-text-indexing"></a>フルテキスト インデックス作成

サンプル データベースは、フルテキスト インデックス作成の使用することができます。 ただし、既定では SQL Server とその機能がインストールされていないに (Azure SQL データベース内の既定で有効には) SQL Server のセットアップ中に選択する必要があります。 そのため、インストール後の手順が必要です。

1. SQL Server Management Studio では、WideWorldImporters データベースに接続し、新しいクエリ ウィンドウを開きます。
2. データベースにフルテキスト インデックス作成の使用を有効にするのには、次の T-SQL コマンドを実行します。`EXECUTE Application.Configuration_ApplyFullTextIndexing`


### <a name="sql-server-audit"></a>SQL Server Audit

適用されます SQL Server。

SQL Server の監査を有効にするには、サーバーの構成が必要です。 WideWorldImporters サンプルの SQL Server 監査を有効にするには、するには、データベースで、次のステートメントを実行します。

    EXECUTE [Application].[Configuration_ApplyAuditing]

Azure SQL Database の監査が構成されているを通じて、 [Azure ポータル](https://portal.azure.com/)です。

### <a name="row-level-security"></a>行レベルのセキュリティ

対象: Azure SQL データベース

行レベルのセキュリティは、WideWorldImporters の bacpac ダウンロードに既定では無効です。 データベースに行レベル セキュリティを有効にするには、次のストアド プロシージャを実行します。

    EXECUTE [Application].[Configuration_ApplyAuditing]


