---
title: SSIS、MDS、および DQS を組み合わせて使用したエンタープライズ情報管理 [チュートリアル] |マイクロソフトドキュメント
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ba09b504-3007-4cb7-8ef8-f01adbf51646
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 29ed5816a3a5fc0af6c5a4ac144557933e3e1a5f
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487721"
---
# <a name="enterprise-information-management-using-ssis-mds-and-dqs-together-tutorial"></a>SSIS、MDS、DQS の組み合わせを使用した Enterprise Information Management [チュートリアル]
  企業の情報管理には、一般に、企業の枠を超えたデータ統合、データのクレンジング、データ照合による重複項目の削除、データの標準化、データの拡充、法的およびコンプライアンス条件に対するデータの準拠、および必要なすべてのセキュリティ設定によるデータの集中管理などの作業が含まれます。  
  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] では、効果的な Enterprise Information Management (EIM) ソリューションに必要なすべてのコンポーネントが 1 つの製品で提供しています。 EIM ソリューションの構築に役立つ主なコンポーネントは次のとおりです。  
  
-   SQL Server Integration Services  
  
-   SQL Server Data Quality Services  
  
-   SQL Server Master Data Services  
  
 SQL Server Integration Services (SSIS) では、ビジネス ワークフロー、データ ウェアハウス、またはマスター データ管理をサポートする包括的な抽出、変換、および読み込み (ETL) のさまざまなソースからデータを統合するための強力な拡張可能プラットフォームを用意しています。 SSIS の概要と一般的な使用方法については、「[統合サービスの概要](https://msdn.microsoft.com/library/ms141263\(SQL.105\).aspx)」を参照してください。  
  
 SQL Server Data Quality Services (DQS) ではデータのクレンジング、照合、標準化、および拡充が可能なため、ビジネス インテリジェンス、データ ウェアハウス、およびトランザクション処理ワークロードに対して信頼できる情報を提供できます。 DQS のビジネス ニーズと DQS のニーズに対する回答については、「[データ品質サービスの概要](https://msdn.microsoft.com/library/ff877917.aspx)」を参照してください。  
  
 SQL Server マスター データ サービス (MDS) の中央データ ハブは、情報の整合性とデータの一貫性がアプリケーション間で変化していないかどうかを確認します。 MDS の重要な機能の簡単な説明については、[マスター データ サービスの概要](../master-data-services/master-data-services-overview-mds.md)に関するトピックを参照してください。  
  
 [EIM](https://msdn.microsoft.com/library/hh403491.aspx)シナリオのクールなデモンストレーションについては、これらの Microsoft EIM テクノロジを使用した EIM ソリューションの実装に関する包括的なガイダンス、[およびエンタープライズ情報管理 (EIM) を](https://go.microsoft.com/fwlink/?LinkId=258672)参照してください。  
  
 このチュートリアルでは、SSIS、MDS、および DQS を組み合わせて、Enterprise Information Management (EIM) ソリューションのサンプルを実装する方法について学習します。 まず、DQS を使用してデータ (メタデータ) についてのナレッジを含むナレッジ ベースを作成し、ナレッジ ベースを使用して Excel ファイル内のデータをクレンジングして、データ内の重複項目を特定および削除するようにデータを照合します。 次に、Excel 用の MDS アドインを使用して、クレンジングおよび照合済みのデータを MDS にアップロードします。 次に、SSIS ソリューションを使用して全体のプロセスを自動化します。 このチュートリアルの SSIS ソリューションでは、Excel ファイルから入力データを読み取りますが、Oracle、Teradata、DB2、Azure SQL データベースなどのさまざまなソースから読み取りできるように拡張できます。  
  
## <a name="prerequisites"></a>前提条件  
  
1.  Microsoft SQL Server 2012 に次のコンポーネントがインストールされていること。  
  
    1.  Integration Services (SSIS)  
  
    2.  マスター データ サービス (MDS)  
  
    3.  Data Quality Services (DQS)  
  
    4.  SQL Server Data Tools  
  
         製品のインストールの詳細については[、「SQL Server 2012 インストール ガイド](../database-engine/install-windows/installation-for-sql-server.md)」を参照してください。  
  
2.  [マスター データ サービス構成マネージャーを使用した MDS の設定](https://msdn.microsoft.com/library/ee633884.aspx)  
  
     マスター データ サービス データベースの作成と構成には、構成マネージャーを使用します。 MDS データベースを作成した後、Web サイトに MDS 用の Web アプリケーション`http://localhost/MDS`(例: ) を作成し、MDS データベースを MDS Web アプリケーションに関連付けます。 MDS Web アプリケーションを作成するには、コンピューターに IIS がインストールされている必要があります。 MDS データベースおよび Web アプリケーションを構成するための前提条件の詳細については[、「Web アプリケーション要件 (マスター データ サービス)」](https://msdn.microsoft.com/library/ee633744.aspx)および[「データベース要件 (マスター データ サービス)」](https://msdn.microsoft.com/library/ee633767.aspx)を参照してください。  
  
3.  [データ品質サーバー インストーラを使用して DQS をインストールおよび構成](https://msdn.microsoft.com/library/hh231682.aspx)する 。 [**スタート]** ボタンをクリックし、[**すべてのプログラム****]** を**クリックします**。 **Data Quality Services**  
  
4.  Microsoft Excel 2010 (32 ビット推奨)  
  
5.  **Excel 用マスター データ サービス アドイン**(コンピュータ上の Excel のバージョンに基づく 32 ビットまたは 64 ビット) は[、ここから](https://www.microsoft.com/download/details.aspx?id=29064)インストールします。 コンピュータにインストールされている Excel のバージョンを確認するには **、Excel**を実行し、メニュー バーの **[ファイル**] をクリックし、[**ヘルプ**] をクリックして右側のウィンドウにバージョンを表示します。 Excel アドインをインストールする前に、Visual Studio 2010 Tools for Office Runtime をインストールする必要があることに注意してください。  
  
6.  (オプション)[Azure マーケットプレース](https://azuremarketplace.microsoft.com/marketplace/)でアカウントを作成する 。 チュートリアルのタスクの 1 つに **、Azure マーケットプレース**(もともと**はデータ マーケット**という名前) アカウントが必要です。 次のタスクに進む場合は、このタスクをスキップできます。  
  
7.  Suppliers.xls ファイルを[Microsoft ダウンロード センター](https://www.microsoft.com/download/details.aspx?id=50426)からダウンロードします。  
  
8.  **64 ビット バージョンの Excel**を使用している場合、DQS ではクレンジングまたは照合結果を Excel ファイルにエクスポートすることはできません。 これは既知の問題です。 この問題を回避するには、次の手順を実行します。  
  
    1.  **を**実行します。 SQL Server の既定のインスタンスをインストールした場合、DQSinstaller.exe ファイルは C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn に格納されます。 DQSInstaller.exe ファイルをダブルクリックします。  
  
    2.  [**マスター データ サービス構成マネージャー**] で、[**データベースの選択**] をクリックし、既存の**MDS**データベースを選択して、[**アップグレード**] をクリックします。  
  
## <a name="lessons"></a>レッスン  
  
|レッスン|簡単な説明|このレッスンの推定所要時間 (分単位)|  
|------------|-----------------------|------------------------------------------------|  
|[レッスン 1: Suppliers DQS ナレッジ ベースを作成する](../../2014/tutorials/lesson-1-creating-the-suppliers-dqs-knowledge-base.md)|このレッスンでは **、Suppliers**という名前の DQS ナレッジ ベースを作成します。|60|  
|[レッスン 2: Suppliers ナレッジ ベースを使用して仕入先データをクレンジングする](../../2014/tutorials/lesson-2-cleansing-supplier-data-using-the-suppliers-knowledge-base.md)|このレッスンでは、最初のレッスンで作成した仕入先ナレッジ ベースを使用して、Excel ファイル内の**仕入先**データをクレンジングする DQS プロジェクトを作成して実行します。|45|  
|[レッスン 3: データを照合して仕入先の一覧から重複を削除する](../../2014/tutorials/lesson-3-matching-data-to-remove-duplicates-from-supplier-list.md)|このレッスンでは、照合アクティビティを実行するための DQS プロジェクトを作成し、クレンジング済みの仕入先一覧から重複項目を特定して削除します。|45|  
|[レッスン 4: MDS に仕入先データを格納する](../../2014/tutorials/lesson-4-storing-supplier-data-in-mds.md)|このレッスンでは **、Excel 用 MDS アドイン**を使用して、クレンジングされた一致した業者データをマスター データ サービス (MDS) にアップロードします。|45|  
|[レッスン 5: SSIS を使用してクレンジングと照合を自動化する](../../2014/tutorials/lesson-5-automating-the-cleansing-and-matching-using-ssis.md)|このレッスンでは、DQS を使用して入力データをクレンジングし、重複項目を削除するためにクレンジングしたデータを照合して、クレンジングおよび照合済みのデータを MDS に自動的に保存する SSIS ソリューションを作成します。|75|  
  
## <a name="next-steps"></a>次の手順  
 チュートリアルを開始するには、最初のレッスン「レッスン[1: 仕入先 DQS ナレッジ ベースの作成](../../2014/tutorials/lesson-1-creating-the-suppliers-dqs-knowledge-base.md)」に進みます。  
  
  
