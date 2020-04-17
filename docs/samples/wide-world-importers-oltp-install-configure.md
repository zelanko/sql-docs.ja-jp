---
title: サンプル データベースをインストールして構成する
description: 以下の手順に従って、SQL Server 管理スタジオを使用して、WideWorldImporters サンプル データベースをダウンロード、インストール、および構成します。
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.date: 04/04/2018
ms.reviewer: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
ms.custom: seo-lt-2019
ms.openlocfilehash: 355eaa254fcc7bb6cd4aa9a39c2cbcb269d88396
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487071"
---
# <a name="installation-and-configuration"></a>インストールと構成
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
ワイド ワールド インポーター OLTP データベースのインストールと構成の手順。

## <a name="prerequisites"></a>前提条件

- [SQL Server 2016](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016) (またはそれ以上) または[Azure SQL データベース](https://azure.microsoft.com/services/sql-database/)。 完全版のサンプルでは、SQL Server 評価版/開発者/エンタープライズ エディションを使用します。
- [SQL サーバー管理スタジオ](../ssms/download-sql-server-management-studio-ssms.md) 最良の結果を得るには、2016 年 6 月以降のリリースを使用してください。

## <a name="download"></a>ダウンロード

サンプルの最新リリース:

[世界の輸入業者リリース](https://go.microsoft.com/fwlink/?LinkID=800630)

SQL Server または Azure SQL データベースのエディションに対応するサンプルの WideWorldImporters データベース バックアップ/バクパックをダウンロードします。

サンプル データベースを再作成するソース コードは、次の場所から入手できます。 サンプルを再作成すると、データ生成にランダムな要因があるため、データにわずかな違いが生じることに注意してください。

[世界の輸入業者](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers/sample-scripts)

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
5. [**データベースの設定]** で、データベース名を*WideWorldImporters*に変更し、使用する対象エディションとサービスの目的を選択します。
6. [**次へ**] をクリックし **、[完了] を**クリックして、展開を開始します。 P1 で完了するまで数分かかります。 低い価格レベルが必要な場合は、新しい P1 データベースにインポートしてから、価格レベルを希望のレベルに変更することをお勧めします。

## <a name="configuration"></a>構成

### <a name="full-text-indexing"></a>フルテキスト インデックス作成

サンプル データベースでは、フルテキスト インデックスを使用できます。 ただし、この機能は SQL Server では既定ではインストールされません。 したがって、インストール後の手順が必要です。

1. SQL Server 管理スタジオで、WideWorldImporters データベースに接続し、新しいクエリ ウィンドウを開きます。
2. 次の T-SQL コマンドを実行して、データベースでフルテキスト インデックスを使用できるようにします。`EXECUTE Application.Configuration_ApplyFullTextIndexing`


### <a name="sql-server-audit"></a>SQL Server Audit

適用対象: SQL Server

SQL Server で監査を有効にするには、サーバー構成が必要です。 ワイドワールドインポートのサンプルの SQL Server 監査を有効にするには、データベースで次のステートメントを実行します。

    EXECUTE [Application].[Configuration_ApplyAuditing]

Azure SQL データベースでは、監査は[Azure ポータル](https://portal.azure.com/)を通じて構成されます。

### <a name="row-level-security"></a>行レベルのセキュリティ

適用先: Azure SQL データベース

行レベルセキュリティは、WideWorldImportersのbacpacダウンロードではデフォルトでは有効になっていません。 データベースで行レベル セキュリティを有効にするには、次のストアド プロシージャを実行します。

    EXECUTE [Application].[Configuration_ApplyRowLevelSecurity]

