---
title: SQL Server から Azure SQL Data Warehouse にデータを読み込む (SSIS) | Microsoft Docs
description: さまざまなデータ ソースから SQL Data Warehouse にデータを移動するための SQL Server Integration Services (SSIS) パッケージを作成する方法を示します。
documentationcenter: NA
ms.service: sql-data-warehouse
ms.component: data-movement
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.custom: loading
ms.date: 04/04/2018
ms.author: douglasl
author: douglaslMS
manager: craigg-msft
ms.openlocfilehash: 84295d9d1e43a9d10724ab8381aa4308f50c8513
ms.sourcegitcommit: abd71294ebc39695d403e341c4f77829cb4166a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2018
ms.locfileid: "36887408"
---
# <a name="load-data-from-sql-server-to-azure-sql-data-warehouse-with-sql-server-integration-services-ssis"></a>SQL Server Integration Services (SSIS) を使用して SQL Server から Azure SQL Data Warehouse にデータを読み込む

SQL Server Integration Services (SSIS) パッケージを作成して、SQL Server から [Azure SQL Data Warehouse](/azure/sql-data-warehouse/index) にデータを読み込みます。 SSIS データ フローを通過するときに、必要に応じてデータを再構築、変換、およびクレンジングすることができます。

このチュートリアルでは、次の作業を行います。

* Visual Studio で新しい Integration Services プロジェクトを作成する。
* データ ソースに接続する。SQL Server (ソースとして) および SQL Data Warehouse (変換先として) を含む。
* データをソースから変換先に読み込むための SSIS パッケージを設計する。
* SSIS パッケージを実行してデータを読み込む。

このチュートリアルでは、SQL Server をデータ ソースとして使用します。 SQL Server の場合は、オンプレミスでも Azure 仮想マシンでも実行することができます。

## <a name="basic-concepts"></a>基本的な概念
このパッケージは SSIS での処理の単位です。 関連パッケージがプロジェクト内でグループ化されます。 SQL Server Data Tools を使用して Visual Studio でプロジェクトの作成およびパッケージの設計を行います。 設計プロセスは視覚的なプロセスであり、ツールボックスからデザイン画面にコンポーネントをドラッグ アンド ドロップし、コンポーネント同士を接続し、それらのプロパティを設定します。 パッケージが完成したら、包括的な管理、監視、およびセキュリティ保護のために必要に応じてパッケージを SQL Server に配置することができます。

## <a name="options-for-loading-data-with-ssis"></a>SSIS を使用してデータを読み込むためのオプション
SQL Server Integration Services (SSIS) とは、SQL Data Warehouse に接続するため、およびデータを読み込みのためのさまざまなオプションを提供する柔軟性に優れたツール セットです。

1. ADO NET 変換先を使用して、SQL Data Warehouse に接続する。 ADO NET 変換先には最小限の構成オプションが含まれているので、このチュートリアルではこれを使用します。
2. OLE DB 変換先を使用して SQL Data Warehouse に接続する。 このオプションは ADO NET 変換先よりも若干優れたパフォーマンスを発揮します。
3. Azure Blob Upload Task を使用して、Azure Blob Storage でデータのステージングを行う。 次に、SSIS の SQL 実行タスクを使用して、SQL Data Warehouse にデータを読み込む Polybase スクリプトを起動します。 このオプションは、ここに示した 3 つのオプションの中で最も高いパフォーマンスを提供します。 Azure BLOB アップロード タスクを取得するには、「[Microsoft SQL Server 2016 Integration Services Feature Pack for Azure][Microsoft SQL Server 2016 Integration Services Feature Pack for Azure]」をダウンロードしてください。 Polybase の詳細については、「[PolyBase Guide][PolyBase Guide]」 (PolyBase ガイド) を参照してください。

## <a name="before-you-start"></a>開始前の準備
このチュートリアルの手順を実行するには、次のものが必要です。

1. **SQL Server Integration Services (SSIS)**. SSIS は SQL Server のコンポーネントであり、使用するには SQL Server の評価版またはライセンス版が必要です。 SQL Server 2016 Preview の評価版を取得するには、「[SQL Server 評価版ソフトウェア][SQL Server Evaluations]」を参照してください。
2. **Visual Studio**. 無料の Visual Studio Community Edition を取得するには、「[Visual Studio Community][Visual Studio Community]」を参照してください。
3. **Visual Studio 用 SQL Server Data Tools (SSDT)**。 Visual Studio 用 SQL Server Data Tools を取得するには、「[SQL Server Data Tools (SSDT) のダウンロード][Download SQL Server Data Tools (SSDT)]」を参照してください。
4. **サンプル データ**。 このチュートリアルでは、SQL Data Warehouse に読み込むソース データとして、SQL Server の AdventureWorks サンプル データベースに格納されているサンプル データを使用します。 AdventureWorks サンプル データベースを取得するには、「[AdventureWorks 2014 Sample Databases][AdventureWorks 2014 Sample Databases]」 (AdventureWorks 2014 のサンプル データベース) を参照してください。
5. **SQL Data Warehouse データベースとアクセス許可**。 このチュートリアルでは、SQL Data Warehouse のインスタンスに接続し、そのインスタンスにデータを読み込みます。 テーブルを作成してデータを読み込むためのアクセス許可が必要です。
6. **ファイアウォール規則**。 SQL Data Warehouse にデータをアップロードするには、事前にローカル コンピューターの IP アドレスを使用して SQL Data Warehouse に対してファイアウォール規則を作成しておく必要があります。

## <a name="step-1-create-a-new-integration-services-project"></a>手順 1: 新しい Integration Services プロジェクトを作成する
1. Visual Studio を起動します。
2. **[ファイル]** メニューの **[新規 | プロジェクト]** を選択します。
3. **[インストール済み | テンプレート | ビジネス インテリジェンス | Integration Services]** のプロジェクトの種類に移動します。
4. **[Integration Services プロジェクト]** を選択します。 **[名前]** と **[場所]** に値を指定し、**[OK]** を選択します。

Visual Studio が開き、新しい Integration Services (SSIS) プロジェクトを作成します。 次に Visual Studio は、プロジェクト内の新しい単一の SSIS パッケージ (Package.dtsx) のためのデザイナーを開きます。 次の画面領域が表示されます。

* 左側には、SSIS コンポーネントの**ツールボックス**。
* 中央には、複数のタブを備えたデザイン画面。 通常は、少なくとも **[制御フロー]** タブと **[データ フロー]** タブを使用します。
* 右側には、**ソリューション エクスプローラー**と **[プロパティ]** ウィンドウ。
  
    ![][01]

## <a name="step-2-create-the-basic-data-flow"></a>手順 2: 基本的なデータ フローを作成する
1. ツールボックスからデザイン画面の中央にデータ フロー タスクをドラッグします (**[制御フロー]** タブ上で)。
   
    ![][02]
2. [データ フロー タスク] をダブルクリックして [データ フロー] タブに切り替えます。
3. ツールボックスにあるその他のソースの一覧から、ADO.NET ソースをデザイン画面にドラッグします。 ソース アダプターが選択された状態で、**[プロパティ]** ウィンドウでその名前を **SQL Server ソース**に変更します。
4. ツールボックスにあるその他の変換先の一覧から、ADO.NET 変換先をデザイン画面にドラッグし、ADO.NET ソースの下に配置します。 変換先アダプターが選択された状態で、**[プロパティ]** ウィンドウでその名前を **SQL DW 変換先**に変更します。
   
    ![][09]

## <a name="step-3-configure-the-source-adapter"></a>手順 3: ソース アダプターを構成する
1. ソース アダプターをダブルクリックして、**ADO.NET 変換元エディター**を開きます。
   
    ![][03]
2. **ADO.NET 変換元エディター**の **[接続マネージャー]** タブで、**[ADO.NET 接続マネージャー]** リストの横にある **[新規]** ボタンをクリックして、**[ADO.NET の接続マネージャーの構成]** ダイアログ ボックスを開き、このチュートリアルでのデータの読み込み元である SQL Server データベースに対する接続設定を作成します。
   
    ![][04]
3. **[ADO.NET 接続マネージャーの構成]** ダイアログ ボックスで、**[新規]** ボタンをクリックして **[接続マネージャー]** ダイアログ ボックスを開き、新しいデータ接続を作成します。
   
    ![][05]
4. **[接続マネージャー]** ダイアログ ボックスで、次の操作を行います。
   
   1. **[プロバイダー]** で、SqlClient データ プロバイダーを選択します。
   2. **[サーバー名]** に SQL Server の名前を入力します。
   3. **[サーバー ログオン]** セクションで、認証情報を選択または入力します。
   4. **[データベースへの接続]** セクションで、AdventureWorks サンプル データベースを選択します。
   5. **[接続テスト]** をクリックします。
      
       ![][06]
   6. 接続テストの結果をレポートするダイアログ ボックスで、**[OK]** をクリックして、**[接続マネージャー]** ダイアログ ボックスに戻ります。
   7. **[接続マネージャー]** ダイアログ ボックスで、**[OK]** をクリックして **[ADO.NET の接続マネージャーの構成]** ダイアログ ボックスに戻ります。
5. **[ADO.NET の接続マネージャーの構成]** ダイアログ ボックスで、**[OK]** をクリックして、**ADO.NET 変換元エディター**に戻ります。
6. **ADO.NET 変換元エディター**の **[Name of the table or the view]\(テーブルまたはビューの名前\)** リストで、**[Sales.SalesOrderDetail]** テーブルを選択します。
   
    ![][07]
7. **[プレビュー]** をクリックして、**[クエリ結果のプレビュー]** ダイアログ ボックスにソース テーブルの先頭の 200 行のデータを表示します。
   
    ![][08]
8. **[クエリ結果のプレビュー]** ダイアログ ボックスで、**[閉じる]** をクリックして **ADO.NET 変換元エディター**に戻ります。
9. **ADO.NET 変換元エディター**で、**[OK]** をクリックしてデータ ソースの構成を完了します。

## <a name="step-4-connect-the-source-adapter-to-the-destination-adapter"></a>手順 4: ソース アダプターを変換先アダプターに接続する
1. デザイン画面でソース アダプターを選択します。
2. ソース アダプターから延びている青い矢印を選択し、それが変換先エディターの所定の位置に固定されるまでドラッグします。
   
    ![][10]
   
    一般的な SSIS パッケージでは、ソースと変換先の間に SSIS ツールボックスからの他の複数のコンポーネントを使用して、データが SSIS データ フローを通過するときにデータの再構築、変換、およびクレンジングを行うことができます。 この例をできるだけ簡単に保持するには、ソースを直接変換先に接続します。

## <a name="step-5-configure-the-destination-adapter"></a>手順 5: 変換先アダプターを構成する
1. 変換先アダプターをダブルクリックして、**ADO.NET 変換先エディター**を開きます。
   
    ![][11]
2. **ADO.NET 変換先エディター**の **[接続マネージャー]** タブで、**[接続マネージャー]** リストの横にある **[新規]** ボタンをクリックして、**[ADO.NET の接続マネージャーの構成]** ダイアログ ボックスを開き、このチュートリアルでのデータの読み込み先である Azure SQL Data Warehouse データベースに対する接続設定を作成します。
3. **[ADO.NET 接続マネージャーの構成]** ダイアログ ボックスで、**[新規]** ボタンをクリックして **[接続マネージャー]** ダイアログ ボックスを開き、新しいデータ接続を作成します。
4. **[接続マネージャー]** ダイアログ ボックスで、次の操作を行います。
   1. **[プロバイダー]** で、SqlClient データ プロバイダーを選択します。
   2. **[サーバー名]** に、SQL Data Warehouse の名前を入力します。
   3. **[サーバー ログオン]** セクションで、**[SQL Server 認証を使用する]** を選択し、認証情報を選択または入力します。
   4. **[データベースへの接続]** セクションで、既存の SQL Data Warehouse データベースを選択します。
   5. **[接続テスト]** をクリックします。
   6. 接続テストの結果をレポートするダイアログ ボックスで、**[OK]** をクリックして、**[接続マネージャー]** ダイアログ ボックスに戻ります。
   7. **[接続マネージャー]** ダイアログ ボックスで、**[OK]** をクリックして **[ADO.NET の接続マネージャーの構成]** ダイアログ ボックスに戻ります。
5. **[ADO.NET の接続マネージャーの構成]** ダイアログ ボックスで、**[OK]** をクリックして、**ADO.NET 変換先エディター**に戻ります。
6. **ADO.NET 変換先エディター**で、**[Use a table or view]\(テーブルまたはビューの使用\)** リストの横にある **[新規]** をクリックして **[テーブルの作成]** ダイアログ ボックスを開き、ソース テーブルと一致する列リストが含まれた新しい変換先テーブルを作成します。
   
    ![][12a]
7. **[テーブルの作成]** ダイアログ ボックスで、次の操作を行います。
   
   1. 変換先テーブルの名前を **SalesOrderDetail** に変更します。
   2. **rowguid** 列を削除します。 SQL Data Warehouse では、**uniqueidentifier** データ型はサポートされていません。
   3. **[LineTotal]** 列のデータ型を **[money]** に変更します。 SQL Data Warehouse では、**decimal** データ型はサポートされていません。 サポートされるデータ型については、[CREATE TABLE (Azure SQL Data Warehouse、Parallel Data Warehouse)][CREATE TABLE (Azure SQL Data Warehouse, Parallel Data Warehouse)] に関するページを参照してください。
      
       ![][12b]
   4. **[OK]** をクリックして、テーブルを作成し、**ADO.NET 変換先エディター**に戻ります。
8. **ADO.NET 変換先エディター**で、**[マッピング]** タブを選択して、ソース内の列が変換先の列にどのようにマップされているか確認してください。
   
    ![][13]
9. **[OK]** をクリックして、データ ソースの構成を完了します。

## <a name="step-6-run-the-package-to-load-the-data"></a>手順 6: パッケージを実行してデータを読み込む
ツールバーの **[開始]** ボタンをクリックするか、**[デバッグ]** メニューの **[実行]** オプションのいずれかを選択してパッケージを実行します。

パッケージが実行を開始すると、アクティビティを示す黄色の糸車と、これまでに処理された行数が表示されます。

![][14]

パッケージが実行を終了すると、成功したことを示す緑色のチェックマークと、ソースから変換先に読み込まれたデータの行数の合計が表示されます。

![][15]

これで、 SQL Server Integration Services を使用して Azure SQL Data Warehouse にデータを読み込むことに成功しました。

## <a name="next-steps"></a>次の手順
* SSIS データ フローの詳細について説明します。 ここから開始: [データ フロー][Data Flow]。
* デザイン環境でパッケージのデバッグおよびトラブルシューティングを行う方法について説明します。 こちらから開始: [パッケージ開発のトラブルシューティング ツール][Troubleshooting Tools for Package Development]。
* Integration Services サーバーまたは別の保存場所に SSIS プロジェクトおよびパッケージを配置する方法について説明します。 こちらから開始: [プロジェクトとパッケージの展開][Deployment of Projects and Packages]。

<!-- Image references -->
[01]:  ./media/load-data-to-sql-data-warehouse/ssis-designer-01.png
[02]:  ./media/load-data-to-sql-data-warehouse/ssis-data-flow-task-02.png
[03]:  ./media/load-data-to-sql-data-warehouse/ado-net-source-03.png
[04]:  ./media/load-data-to-sql-data-warehouse/ado-net-connection-manager-04.png
[05]:  ./media/load-data-to-sql-data-warehouse/ado-net-connection-05.png
[06]:  ./media/load-data-to-sql-data-warehouse/test-connection-06.png
[07]:  ./media/load-data-to-sql-data-warehouse/ado-net-source-07.png
[08]:  ./media/load-data-to-sql-data-warehouse/preview-data-08.png
[09]:  ./media/load-data-to-sql-data-warehouse/source-destination-09.png
[10]:  ./media/load-data-to-sql-data-warehouse/connect-source-destination-10.png
[11]:  ./media/load-data-to-sql-data-warehouse/ado-net-destination-11.png
[12a]: ./media/load-data-to-sql-data-warehouse/destination-query-before-12a.png
[12b]: ./media/load-data-to-sql-data-warehouse/destination-query-after-12b.png
[13]:  ./media/load-data-to-sql-data-warehouse/column-mapping-13.png
[14]:  ./media/load-data-to-sql-data-warehouse/package-running-14.png
[15]:  ./media/load-data-to-sql-data-warehouse/package-success-15.png

<!-- Article references -->

<!-- MSDN references -->
[PolyBase Guide]: ../relational-databases/polybase/polybase-guide.md
[Download SQL Server Data Tools (SSDT)]: ../ssdt/download-sql-server-data-tools-ssdt.md
[CREATE TABLE (Azure SQL Data Warehouse, Parallel Data Warehouse)]: ../t-sql/statements/create-table-azure-sql-data-warehouse.md
[Data Flow]: ./data-flow/data-flow.md
[Troubleshooting Tools for Package Development]: ./troubleshooting/troubleshooting-tools-for-package-development.md
[Deployment of Projects and Packages]: ./packages/deploy-integration-services-ssis-projects-and-packages.md

<!--Other Web references-->
[Microsoft SQL Server 2016 Integration Services Feature Pack for Azure]: http://go.microsoft.com/fwlink/?LinkID=626967
[SQL Server Evaluations]: https://www.microsoft.com/evalcenter/evaluate-sql-server-2016
[Visual Studio Community]: https://www.visualstudio.com/products/visual-studio-community-vs.aspx
[AdventureWorks 2014 Sample Databases]: https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks
