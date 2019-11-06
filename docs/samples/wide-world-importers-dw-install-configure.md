---
title: OLAP の WideWorldImporters サンプル データベースのインストールし、構成 - SQL |Microsoft Docs
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.custom: ''
ms.date: 08/04/2018
ms.reviewer: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2016||>=sql-server-linux-2017||=azure-sqldw-latest||>=aps-pdw-2016||=sqlallproducts-allversions||=azuresqldb-mi-current'
ms.openlocfilehash: ed3c5f1a4f2168196a651aea64c9c88311a197b9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68104252"
---
# <a name="wideworldimportersdw-installation-and-configuration"></a>WideWorldImportersDW のインストールと構成
[!INCLUDE[appliesto-ss-xxxx-asdw-pdw-md](../includes/appliesto-ss-xxxx-asdw-pdw-md.md)]
WideWorldImportersDW データベースのインストールと構成の手順です。

- [SQL Server 2016](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016) (またはそれ以降) または[Azure SQL Database](https://azure.microsoft.com/services/sql-database/)します。 完全なバージョンのサンプルを使用するには、SQL Server の評価、Developer、または Enterprise Edition を使用します。
- [SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md)。 最善の結果を得るには、2016 年 6 月リリース以降を使用してください。

## <a name="download"></a>ダウンロード

サンプルの最新リリース:

[wide-world-importers-release](https://go.microsoft.com/fwlink/?LinkID=800630)

SQL Server または Azure SQL データベースのエディションに対応するサンプル WideWorldImportersDW データベースのバックアップ/bacpac をダウンロードしてください。

サンプル データベースを再作成するソース コードは、以下の場所から使用可能です。 データ カタログの作成は、OLTP データベース (WideWorldImporters) から ETL に基づいていることに注意してください。

[wide-world-importers-source](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers/wwi-dw-database-scripts)

## <a name="install"></a>インストール


### <a name="sql-server"></a>SQL Server

SQL Server インスタンスにバックアップを復元するには、Management Studio を使用できます。

1. SQL Server Management Studio を開き、対象の SQL Server インスタンスに接続します。
2. **データベース**ノードを右クリックし、**Restore Database** を選択します。
3. 選択**デバイス** ボタンをクリックします **。**
4. ダイアログ ボックスで**バックアップ デバイスの選択**、 をクリックして**追加**サーバーのファイル システム内のデータベースのバックアップに移動して、バックアップを選択します。 **[OK]** をクリックします。
5. 必要に応じて、データのターゲットの場所を変更し、ログ ファイルで、**ファイル**ウィンドウ。 ベスト プラクティスとしてデータを配置し、ログ ファイルを別のドライブにあるに注意してください。
6. **[OK]** をクリックします。 これにより、データベースの復元が開始されます。 完了した後、データベース、SQL Server インスタンスにインストールされている WideWorldImporters 必要があります。

### <a name="azure-sql-database"></a>Azure SQL データベース

新しい SQL Database には、bacpac をインポートするには、Management Studio を使用できます。

1. (省略可能)Azure で SQL Server をまだ必要はない場合に移動、 [Azure portal](https://portal.azure.com/)し、新しい SQL データベースを作成します。 途中でデータベースを作成、サーバーを作成します。 サーバーのメモしてをおきます。
   - 参照してください[このチュートリアル](https://azure.microsoft.com/documentation/articles/sql-database-get-started/)分でデータベースを作成するには
2. SQL Server Management Studio を開き、Azure でサーバーに接続します。
3. 右クリックし、**データベース**ノード、および選択**データ層アプリケーションのインポート**します。
4. **設定のインポート**選択**ローカル ディスクからインポート**し、ファイル システムから、サンプル データベースの bacpac を選択します。
5. **データベース設定**データベース名を変更して*WideWorldImportersDW*を使用するターゲット エディションとサービス目標を選択します。
6. をクリックして**次**と**完了**展開を開始します。 完了するまでに数分をかかります。 S2 より低いサービス目標を指定する場合は、長い時間がかかる場合があります。

## <a name="configuration"></a>構成

[SQL Server 2016 (以降) の開発者、構造体、Enterprise Evaluation Edition に適用されます]

サンプル データベースは、Hadoop または Azure blob ストレージ内のクエリ ファイルを使用して、PolyBase のこと。 ただし、SQL Server では既定でその機能がインストールされていない - SQL Server のセットアップ中に選択する必要があります。 そのため、インストール後の手順が必要です。

1. SQL Server Management studio では、WideWorldImportersDW データベースに接続し、新しいクエリ ウィンドウを開きます。
2. PolyBase を使用して、データベースで有効にするのには、次の T-SQL コマンドを実行します。

   [アプリケーション] を実行します。[Configuration_ApplyPolyBase]
