---
title: "レッスン 2: 接続情報 (Reporting Services) を指定する |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/23/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 54405a3a-d7fa-4d95-8963-9aa224e5901e
caps.latest.revision: 53
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 4d0667dec1b59d5560ca24176634dddc5d6d8d18
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="lesson-2-specifying-connection-information-reporting-services"></a>レッスン 2 : 接続情報の指定 (Reporting Services)
追加した後、[!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)]を定義する必要があります、レッスン 1 でチュートリアル プロジェクトにレポートを改ページ調整された、*データ ソース*、リレーショナル データベース、多次元データベース、または別のソースからデータにアクセスするレポートを使用して接続情報です。  
  
このレッスンで使用し、[!INCLUDE[ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)]サンプル データベースをデータ ソースとして。 このチュートリアルではこのデータベースがの既定のインスタンスに配置されている[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../includes/ssde-md.md)]ローカル コンピューターにインストールします。  
  
### <a name="to-set-up-a-connection"></a>接続を設定するには  
  
1.  **レポート データ** ウィンドウで、をクリックして**新規** をクリックし、**データ ソース**です。  
**レポート データ** ペインが表示されていない場合は、 **[表示]** メニューの **[レポート データ]**をクリックします。  

    ![ssrs-table-tutorial-2-new-data-source](../reporting-services/media/ssrs-table-tutorial-2-new-data-source.png)
  
   2.  **[名前]**に、「 *AdventureWorks2014*」と入力します。  
  
3.  **[埋め込み接続]** が選択されていることを確認します。  
  
4.  **[種類]**で **[Microsoft SQL Server]**を選択します。  
  
5.  **[接続文字列]**に次を入力します。  
  
    ```  
    Data source=localhost; initial catalog=AdventureWorks2014  
    ```  
  
     この接続文字列は、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]、レポート サーバー、および [!INCLUDE[ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)] データベースがすべてローカル コンピューターにインストールされていることと、ユーザーが [!INCLUDE[ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)] データベースにログオンする権限を持っていることが前提となります。 AdventureWorks2014 データベースがローカル コンピューターにない場合は、接続文字列を変更して、置換*localhost*データベース サーバー インスタンスの名前に置き換えます。
  
     >[!NOTE]  
    >[!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services または名前付きインスタンスを使用している場合は、接続文字列にインスタンス情報を含める必要があります。  
    >  
    >`Data source=localhost\SQLEXPRESS; initial catalog=AdventureWorks2014`  
    >  
    >接続文字列の詳細については、次を参照してください。 [Data Connections, Data Sources, and Connection Strings in Reporting Services](../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)をクリックします。  
     
  
6.  左ペインで **[資格情報]** をクリックし、 **[Windows 認証 (統合セキュリティ) を使用する]**をクリックします。  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)] データ ソース **AdventureWorks2014** が **レポート データ** ペインに追加されます。  
![ssrs_adventureworks_datasource](../reporting-services/media/ssrs-adventureworks-datasource.png)  
## <a name="next-task"></a>次の作業  
[!INCLUDE[ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)] サンプル データベースへの接続が正常に定義されました。 次に、レポートを作成します。 「[レッスン 3: テーブル レポートのデータセットの定義 (Reporting Services)](../reporting-services/lesson-3-defining-a-dataset-for-the-table-report-reporting-services.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
[Data Connections, Data Sources, and Connection Strings in Reporting Services](../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)  
  
  
  


