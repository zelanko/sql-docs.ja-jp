---
title: SSIS、MDS、および [チュートリアル] の [DQS の組み合わせを使用した Enterprise Information Management |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.topic: conceptual
ms.assetid: ba09b504-3007-4cb7-8ef8-f01adbf51646
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 9d03470d21532ce097ba753fb8073a5685ccb9f8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48122632"
---
# <a name="enterprise-information-management-using-ssis-mds-and-dqs-together-tutorial"></a>SSIS、MDS、DQS の組み合わせを使用した Enterprise Information Management [チュートリアル]
  企業の情報管理には、一般に、企業の枠を超えたデータ統合、データのクレンジング、データ照合による重複項目の削除、データの標準化、データの拡充、法的およびコンプライアンス条件に対するデータの準拠、および必要なすべてのセキュリティ設定によるデータの集中管理などの作業が含まれます。  
  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] では、効果的な Enterprise Information Management (EIM) ソリューションに必要なすべてのコンポーネントが 1 つの製品で提供しています。 EIM ソリューションの構築に役立つ主なコンポーネントは次のとおりです。  
  
-   SQL Server Integration Services  
  
-   SQL Server Data Quality Services  
  
-   SQL Server マスター データ サービス  
  
 SQL Server Integration Services (SSIS) では、ビジネス ワークフロー、データ ウェアハウス、またはマスター データ管理をサポートする包括的な抽出、変換、および読み込み (ETL) のさまざまなソースからデータを統合するための強力な拡張可能プラットフォームを用意しています。 参照してください[Integration Services の概要](http://msdn.microsoft.com/library/ms141263\(SQL.105\).aspx)SSIS の概要と一般的なトピックを使用します。  
  
 SQL Server Data Quality Services (DQS) ではデータのクレンジング、照合、標準化、および拡充が可能なため、ビジネス インテリジェンス、データ ウェアハウス、およびトランザクション処理ワークロードに対して信頼できる情報を提供できます。 参照してください[Data Quality Services の概要](http://msdn.microsoft.com/library/ff877917.aspx)DQS とどのようにニーズに対する DQS のビジネス ニーズのためのトピックです。  
  
 SQL Server マスター データ サービス (MDS) の中央データ ハブは、情報の整合性とデータの一貫性がアプリケーション間で変化していないかどうかを確認します。 参照してください[マスター データ サービスの概要](../master-data-services/master-data-services-overview-mds.md)MDS の重要な機能の簡単な説明のトピックです。  
  
 参照してください[クレンジングと EIM テクノロジを使用して、一致するマスター データ](http://msdn.microsoft.com/library/hh403491.aspx)EIM ソリューションのこれらの Microsoft EIM テクノロジを組み合わせて使用し、ウォッチの実装についての包括的なホワイト ペーパー [EnterpriseInformation Management (EIM): SSIS、DQS、および MDS がまとめて終了する](http://go.microsoft.com/fwlink/?LinkId=258672)EIM シナリオのデモについてすばらしいビデオ。  
  
 このチュートリアルでは、SSIS、MDS、および DQS を組み合わせて、Enterprise Information Management (EIM) ソリューションのサンプルを実装する方法について学習します。 まず、DQS を使用してデータ (メタデータ) についてのナレッジを含むナレッジ ベースを作成し、ナレッジ ベースを使用して Excel ファイル内のデータをクレンジングして、データ内の重複項目を特定および削除するようにデータを照合します。 次に、Excel 用の MDS アドインを使用して、クレンジングおよび照合済みのデータを MDS にアップロードします。 次に、SSIS ソリューションを使用して全体のプロセスを自動化します。 このチュートリアルでは、SSIS ソリューションは Excel ファイルから入力データを読み取りますが、Oracle、Teradata、DB2、Windows Azure SQL Database などのさまざまなソースから読み取ることもできます。  
  
## <a name="prerequisites"></a>前提条件  
  
1.  Microsoft SQL Server 2012 に次のコンポーネントがインストールされていること。  
  
    1.  Integration Services (SSIS)  
  
    2.  マスター データ サービス (MDS)  
  
    3.  Data Quality Services (DQS)  
  
    4.  SQL Server Data Tools  
  
         参照してください[SQL Server 2012 インストール ガイド](../database-engine/install-windows/installation-for-sql-server.md)詳細については、製品をインストールします。  
  
2.  [マスター データ サービス構成マネージャーを使用して MDS を構成します。](http://msdn.microsoft.com/library/ee633884.aspx)  
  
     マスター データ サービス データベースの作成と構成には、構成マネージャーを使用します。 MDS データベースを作成したら、web でアプリケーションを作成 MDS 用 web サイト (例: [ http://localhost/MDS ](http://localhost/MDS)) し、MDS データベースを MDS web アプリケーションに関連付けます。 MDS Web アプリケーションを作成するには、コンピューターに IIS がインストールされている必要があります。 参照してください[Web アプリケーションの要件 (マスター データ サービス)](http://msdn.microsoft.com/library/ee633744.aspx)と[データベース要件 (マスター データ サービス)](http://msdn.microsoft.com/library/ee633767.aspx)詳細については、MDS データベースと web アプリケーションを構成するための前提条件です。  
  
3.  [Data Quality Server インストーラーを使用して構成する DQS のインストールと](http://msdn.microsoft.com/library/hh231682.aspx)します。 をクリックして**開始**、 をクリックして**すべてのプログラム**、 をクリックして**Microsoft SQL Server 2014**、 をクリックして**Data Quality Services**をクリックして**Data Quality Server インストーラー**します。  
  
4.  Microsoft Excel 2010 (32 ビット推奨)  
  
5.  インストール**マスター データ サービス アドインの Excel** (32 ビットまたは 64 ビットに基づいて、コンピューター上にある Excel のバージョン) から[ここ](http://www.microsoft.com/download/details.aspx?id=29064)します。 コンピューターにインストールされている Excel のバージョンを見つけるには実行**Excel**、 をクリックして**ファイル**をクリックし、メニュー バー**ヘルプ**右側のウィンドウでバージョンを確認します。 Excel アドインをインストールする前に、for Office Runtime Visual Studio 2010 Tools をインストールする必要があるに注意してください。  
  
6.  (省略可能)持つアカウントを作成する[Windows Azure Marketplace](https://datamarket.azure.com/)します。 チュートリアルのタスクの 1 つ必要がある場合、 **Azure Marketplace** (元の名前**データ マーケット**) アカウント。 次のタスクに進む場合は、このタスクをスキップできます。  
  
7.  Suppliers.xls ファイルをダウンロード[Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkId=271504)します。  
  
8.  DQS はクレンジングまたは照合では、使用する場合を Excel ファイルに結果をエクスポートすることを許可しない**64 ビット バージョンの Excel**します。 これは既知の問題です。 この問題を回避するには、次の手順を実行します。  
  
    1.  実行**DQLInstaller.exe – アップグレード**します。 SQL Server の既定のインスタンスをインストールした場合、DQSinstaller.exe ファイルは C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn に格納されます。 DQSInstaller.exe ファイルをダブルクリックします。  
  
    2.  **Master Data Services 構成マネージャー**、 をクリックして**データベースの選択**既存の選択、 **MDS**データベースをクリックして**をアップグレード**.  
  
## <a name="lessons"></a>レッスン  
  
|レッスン|簡単な説明|このレッスンの推定所要時間 (分単位)|  
|------------|-----------------------|------------------------------------------------|  
|[レッスン 1: Suppliers DQS ナレッジ ベースを作成する](../../2014/tutorials/lesson-1-creating-the-suppliers-dqs-knowledge-base.md)|このレッスンでという名前の DQS ナレッジ ベースを作成する**Suppliers**します。|60|  
|[レッスン 2: Suppliers ナレッジ ベースを使用して仕入先データをクレンジングする](../../2014/tutorials/lesson-2-cleansing-supplier-data-using-the-suppliers-knowledge-base.md)|このレッスンで作成し、DQS プロジェクトを使用して Excel ファイルの仕入先データのクレンジングを実行、 **Suppliers**最初のレッスンで作成したナレッジ ベース。|45|  
|[レッスン 3: データを照合して仕入先の一覧から重複を削除する](../../2014/tutorials/lesson-3-matching-data-to-remove-duplicates-from-supplier-list.md)|このレッスンでは、照合アクティビティを実行するための DQS プロジェクトを作成し、クレンジング済みの仕入先一覧から重複項目を特定して削除します。|45|  
|[レッスン 4: MDS に仕入先データを格納する](../../2014/tutorials/lesson-4-storing-supplier-data-in-mds.md)|このレッスンでクレンジングおよび照合済みの仕入先データ マスター データ サービス (MDS) を使用してアップロードする、 **MDS アドインの Excel**します。|45|  
|[レッスン 5: SSIS を使用してクレンジングと照合を自動化する](../../2014/tutorials/lesson-5-automating-the-cleansing-and-matching-using-ssis.md)|このレッスンでは、DQS を使用して入力データをクレンジングし、重複項目を削除するためにクレンジングしたデータを照合して、クレンジングおよび照合済みのデータを MDS に自動的に保存する SSIS ソリューションを作成します。|75|  
  
## <a name="next-steps"></a>次の手順  
 チュートリアルを開始するには、最初のレッスンに進んでください。:[レッスン 1: Suppliers DQS ナレッジ ベースを作成する](../../2014/tutorials/lesson-1-creating-the-suppliers-dqs-knowledge-base.md)します。  
  
  
