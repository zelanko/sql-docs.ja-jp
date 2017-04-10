---
title: "レポートまたはモデルを共有データ ソースにバインドする (SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "共有データ ソース [Reporting Services]"
  - "データ ソース [Reporting Services], 共有"
ms.assetid: 23cc15f2-2883-48e2-bc6c-fa0ab61a2e21
caps.latest.revision: 11
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 11
---
# レポートまたはモデルを共有データ ソースにバインドする (SSRS)
  レポートまたはモデルをテスト サーバーから実稼働サーバーに移動するときなど、ファイルをローカル コンピューターに保存した後で別のレポート サーバーにアップロードする操作が必要になる場合があります。 レポートまたはモデルを新しいサーバーにアップロードしたときは、新しいレポート サーバー上に格納されている共有データ ソースにレポートまたはモデルを再バインドする必要があります。 レポートまたはモデルの再バインドを行わないと、レポートまたはモデルが新しいレポート サーバーからアクセスされたときに正常に動作しない場合があります。  
  
> [!IMPORTANT]  
>  レポートまたはモデルを共有データ ソースに再バインドする前に、データ ソースがレポート サーバーまたは SharePoint ライブラリに存在している必要があります。 データ ソースの詳細については、「[共有データ ソースを作成、変更、および削除する (SSRS)](../../reporting-services/report-data/create-modify-and-delete-shared-data-sources-ssrs.md)」を参照してください。  
  
### ネイティブ モードで実行されているレポート サーバー上の共有データ ソースにレポートまたはモデルをバインドするには  
  
1.  **レポート マネージャー**で、サーバーにアップロードしたレポートまたはモデルの名前をクリックします。  
  
     [プロパティ] タブが開きます。  
  
2.  **[データ ソース]** をクリックします。  
  
3.  **[参照]** をクリックし、レポートまたはモデルをバインドするデータ ソースを参照します。  
  
4.  データ ソースを選択し、**[OK]** をクリックします。  
  
5.  **[適用]**をクリックします。  
  
     選択したデータ ソースにレポートまたはモデルがバインドされます。  
  
### SharePoint 統合モードで実行されているレポート サーバー上の共有データ ソースにレポートまたはモデルをバインドするには  
  
1.  まだライブラリが開いていない場合は、クイック起動バーでライブラリの名前をクリックします。 ライブラリの名前が表示されていない場合は、 **[すべてのサイト コンテンツの表示]**をクリックし、ライブラリの名前をクリックします。  
  
2.  レポートまたはモデルをポイントし、下矢印をクリックします。  
  
3.  **[データ ソースの管理]** をクリックします。  
  
4.  **[dataSource1]** をクリックします。  
  
5.  **[接続の種類]** 領域で、**[共有データ ソース]** が選択されていることを確認します。  
  
6.  **[データ ソース リンク]** 領域で、省略記号ボタン ([...]) をクリックします。  
  
7.  使用するデータ ソースを探します。  
  
8.  データ ソースを選択し、**[OK]** をクリックします。  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
10. **[閉じる]**をクリックします。  
  
## 参照  
 [ファイルまたはレポートをアップロードする (レポート マネージャー)](../../reporting-services/reports/upload-a-file-or-report-report-manager.md)   
 [SharePoint ライブラリへのドキュメントのアップロード (Reporting Services の SharePoint モード)](../../reporting-services/report-server-sharepoint/upload-documents-to-a-sharepoint-library-reporting-services-in-sharepoint-mode.md)   
 [共有データ ソースを作成および管理する (Reporting Services の SharePoint 統合モード)](../Topic/Create%20and%20Manage%20Shared%20Data%20Sources%20\(Reporting%20Services%20in%20SharePoint%20Integrated%20Mode\).md)   
 [共有データ ソースを作成、削除、または変更する (レポート マネージャー)](../Topic/Create,%20Delete,%20or%20Modify%20a%20Shared%20Data%20Source%20\(Report%20Manager\).md)   
 [データ接続、データ ソース、および接続文字列 (レポート ビルダーおよび SSRS)](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)   
 [Reporting Services でサポートされるデータ ソース (SSRS)](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md)  
  
  