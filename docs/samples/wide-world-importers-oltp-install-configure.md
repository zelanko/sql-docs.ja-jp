---
title: インストールし、構成の WideWorldImporters サンプル データベース - SQL |Microsoft Docs
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.custom: ''
ms.date: 04/04/2018
ms.reviewer: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6fc303892fdefda350a2bb6513a71226264e50fe
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68067670"
---
# <a name="installation-and-configuration"></a>インストールと構成
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Wide World Importers OLTP データベースのインストールと構成の手順。

## <a name="prerequisites"></a>必須コンポーネント

- [SQL Server 2016](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016) (またはそれ以降) または[Azure SQL Database](https://azure.microsoft.com/services/sql-database/)します。 完全なバージョンのサンプルでは、SQL Server の評価、Developer、または Enterprise Edition を使用します。
- [SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md)。 最善の結果を得るには、2016 年 6 月リリース以降を使用してください。

## <a name="download"></a>ダウンロード

サンプルの最新リリース:

[wide-world-importers-release](https://go.microsoft.com/fwlink/?LinkID=800630)

Bacpac をダウンロード サンプル WideWorldImporters データベースのバックアップ/対応する SQL Server または Azure SQL Database のエディション。

サンプル データベースを再作成するソース コードは、以下の場所から使用可能です。 このサンプルを再作成する原因になるデータをわずかに異なるデータ生成、ランダムな要素であるために注意してください。

[wide-world-importers](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers/wwi-database-scripts)

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
5. **データベース設定**データベース名を変更して*WideWorldImporters*を使用するターゲット エディションとサービス目標を選択します。
6. をクリックして**次**と**完了**展開を開始します。 P1、完了に数分をされます。 価格が低い場合は、層が必要に応じてを新しい P1 データベースにインポートし、必要なレベルに価格レベルを変更することをお勧めします。

## <a name="configuration"></a>構成

### <a name="full-text-indexing"></a>フルテキスト インデックス作成

サンプル データベースは、フルテキスト インデックス作成の使用をこと。 ただし、SQL Server では既定でその機能がインストールされていない - (Azure SQL DB では既定では有効です)、SQL Server セットアップ中に選択する必要があります。 そのため、インストール後の手順が必要です。

1. SQL Server Management studio では、WideWorldImporters データベースに接続し、新しいクエリ ウィンドウを開きます。
2. データベースでフルテキスト インデックス作成の使用を有効にするのには、次の T-SQL コマンドを実行します。  `EXECUTE Application.Configuration_ApplyFullTextIndexing`


### <a name="sql-server-audit"></a>SQL Server Audit

適用対象:SQL Server

SQL Server での監査を有効にするには、サーバーの構成が必要です。 WideWorldImporters サンプルの SQL Server 監査を有効にするには、データベースで、次のステートメントを実行します。

    EXECUTE [Application].[Configuration_ApplyAuditing]

Azure SQL Database で監査が構成されている、 [Azure portal](https://portal.azure.com/)します。

### <a name="row-level-security"></a>行レベルのセキュリティ

適用対象:Azure SQL データベース

行レベル セキュリティは、WideWorldImporters の bacpac のダウンロードで既定では無効です。 をデータベースに行レベル セキュリティを有効にするには、次のストアド プロシージャを実行します。

    EXECUTE [Application].[Configuration_ApplyRowLevelSecurity]

