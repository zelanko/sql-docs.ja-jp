---
title: "レッスン 2 : 接続情報の指定 (Reporting Services) | Microsoft Docs"
ms.custom: ""
ms.date: "05/23/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 54405a3a-d7fa-4d95-8963-9aa224e5901e
caps.latest.revision: 53
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 51
---
# レッスン 2 : 接続情報の指定 (Reporting Services)
チュートリアル プロジェクトにレポートを追加した後、リレーショナル データベース、多次元データベース、その他のリソースのデータにアクセスするためにレポートで使用される接続情報である*データ ソース*を定義する必要があります。  
  
このレッスンでは、[!INCLUDE[ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)] サンプル データベースをデータ ソースとして使用します。 このチュートリアルでは、ローカル コンピューターにインストールされている既定の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] インスタンスにこのデータベースが配置されているものとします。  
  
### 接続を設定するには  
  
1.  **レポート データ** ペインで、**[新規作成]** をクリックし、**[データ ソース…]** をクリックします。  
**レポート データ** ペインが表示されていない場合は、**[表示]** メニューの **[レポート データ]** をクリックします。  
  
   2.  **[名前]** に、「*Adventureworks2014*」と入力します。  
  
3.  **[埋め込み接続]** が選択されていることを確認します。  
  
4.  **[種類]** で **[Microsoft SQL Server]** を選択します。  
  
5.  **[接続文字列]** に次を入力します。  
  
    ```  
    Data source=localhost; initial catalog=AdventureWorks2014  
    ```  
  
この接続文字列は、[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]、レポート サーバー、および [!INCLUDE[ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)] データベースがすべてローカル コンピューターにインストールされていることと、ユーザーが [!INCLUDE[ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)] データベースにログオンする権限を持っていることが前提となります。 AdventureWorks2014 がローカル コンピューターにない場合、接続文字列を変更し、*loclahost* をデータベース サーバー インスタンスの名前に置換します。
   
  
 > [!NOTE]  
 > [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services または名前付きインスタンスを使用している場合は、接続文字列にインスタンス情報を含める必要があります。  
 >   
 > `Data source=localhost\SQLEXPRESS; initial catalog=AdventureWorks2014`  
 >   
 > 接続文字列の詳細については、次を参照してください。  
 > *  [Data Connections, Data Sources, and Connection Strings in Reporting Services](../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)  
    > * [[全般] ([データ ソースのプロパティ] ダイアログ ボックス)](../Topic/Data%20Source%20Properties%20Dialog%20Box,%20General.md)  
        
  
6.  左ペインで **[資格情報]** をクリックし、**[Windows 認証 (統合セキュリティ) を使用する]** をクリックします。  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)] データ ソース [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] が**レポート データ** ペインに追加されます。  
![ssrs_adventureworks_datasource](../reporting-services/media/ssrs-adventureworks-datasource.png)  
## 次の作業  
[!INCLUDE[ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)] サンプル データベースへの接続が正常に定義されました。 次に、レポートを作成します。 「[レッスン 3: テーブル レポートのデータセットの定義 (Reporting Services)](../reporting-services/lesson-3-defining-a-dataset-for-the-table-report-reporting-services.md)」を参照してください。  
  
## 参照  
[[全般] ([データ ソースのプロパティ] ダイアログ ボックス)](../Topic/Data%20Source%20Properties%20Dialog%20Box,%20General.md)  
[Data Connections, Data Sources, and Connection Strings in Reporting Services](../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)  
  
  
  
