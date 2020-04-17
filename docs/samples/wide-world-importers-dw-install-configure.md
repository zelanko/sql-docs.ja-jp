---
title: DW ワイドワールドインポーターサンプルデータベースをインストール&構成する
description: 以下の手順に従って、SQL Server 管理スタジオを使用して、サンプル データベースをダウンロード、インストール、および構成します。
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.date: 08/04/2018
ms.reviewer: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2016||>=sql-server-linux-2017||=azure-sqldw-latest||>=aps-pdw-2016||=sqlallproducts-allversions||=azuresqldb-mi-current'
ms.custom: seo-lt-2019
ms.openlocfilehash: 2f640415ecdc2ae4a48220aeec2a2c78ed79807c
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488553"
---
# <a name="wideworldimportersdw-installation-and-configuration"></a>ワイドワールドインポートーズDWのインストールと構成
[!INCLUDE[appliesto-ss-xxxx-asdw-pdw-md](../includes/appliesto-ss-xxxx-asdw-pdw-md.md)]
ワイドワールドインポートのDWデータベースのインストールと構成の手順。

- [SQL Server 2016](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016) (またはそれ以上) または[Azure SQL データベース](https://azure.microsoft.com/services/sql-database/)。 完全版のサンプルを使用するには、SQL Server 評価版、開発者版、エンタープライズ エディションを使用します。
- [SQL サーバー管理スタジオ](../ssms/download-sql-server-management-studio-ssms.md) 最良の結果を得るには、2016 年 6 月以降のリリースを使用してください。

## <a name="download"></a>ダウンロード

サンプルの最新リリース:

[世界の輸入業者リリース](https://go.microsoft.com/fwlink/?LinkID=800630)

SQL Server または Azure SQL データベースのエディションに対応するサンプルの WideWorldImportersDW データベース バックアップ/バクパックをダウンロードします。

サンプル データベースを再作成するソース コードは、次の場所から入手できます。 データの作成は OLTP データベース (ワイドワールドインポータ) からの ETL に基づいていることに注意してください。

[世界の輸入業者・供給源](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers/sample-scripts)

## <a name="install"></a>インストール


### <a name="sql-server"></a>SQL Server

SQL Server インスタンスにバックアップを復元するには、管理スタジオを使用できます。

1. SQL Server 管理スタジオを開き、ターゲットの SQL Server インスタンスに接続します。
2. **[データベース**] ノードを右クリックし、[**データベースの復元**] をクリックします。
3. [**デバイス] を**選択し、ボタンをクリック**します。**
4. [**バックアップ デバイスの選択**] ダイアログで [ 追加 **]** をクリックし、サーバのファイルシステム内のデータベース バックアップに移動して、バックアップを選択します。 **[OK]** をクリックします。
5. 必要に応じて、[**ファイル**] ウィンドウでデータ ファイルとログ ファイルのターゲットの場所を変更します。 データ ファイルとログ ファイルは、別のドライブに配置することをお勧めします。
6. **[OK]** をクリックします。 これにより、データベースの復元が開始されます。 完了すると、データベースの WideWorldImporters が SQL Server インスタンスにインストールされます。

### <a name="azure-sql-database"></a>Azure SQL データベース

bacpac を新しい SQL データベースにインポートするには、管理スタジオを使用できます。

1. (オプション)Azure に SQL Server がまだない場合は[、Azure ポータル](https://portal.azure.com/)に移動して新しい SQL データベースを作成します。 データベースを作成するプロセスでは、サーバーを作成します。 サーバーをメモします。
   - [このチュートリアル](https://azure.microsoft.com/documentation/articles/sql-database-get-started/)を参照して、数分でデータベースを作成します。
2. SQL Server 管理スタジオを開き、Azure でサーバーに接続します。
3. **[データベース**] ノードを右クリックし、[**データ層アプリケーションのインポート**] を選択します。
4. [**インポート設定]** で [**ローカル ディスクからインポート**] を選択し、ファイル システムからサンプル データベースの bacpac を選択します。
5. データベース**設定**で、データベース名を*WideWorldImportersDW*に変更し、使用する対象エディションとサービスの目的を選択します。
6. [**次へ**] をクリックし **、[完了] を**クリックして、展開を開始します。 この処理は完了までに数分かかります。 S2 より低いサービス目標を指定する場合、時間がかかる場合があります。

## <a name="configuration"></a>構成

[SQL Server 2016 (および後で) 開発者/評価/エンタープライズ エディションに適用されます]

サンプル データベースは、PolyBase を使用して Hadoop または Azure BLOB ストレージ内のファイルをクエリできます。 ただし、SQL Server では、この機能は既定ではインストールされません。 したがって、インストール後の手順が必要です。

1. SQL Server 管理スタジオで、ワイドワールド インポートデータDW データベースに接続し、新しいクエリ ウィンドウを開きます。
2. 次の T-SQL コマンドを実行して、データベースで PolyBase を使用できるようにします。

   [アプリケーション]を実行します。[Configuration_ApplyPolyBase]
