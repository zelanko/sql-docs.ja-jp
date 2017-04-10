---
title: "データ ソースの変換 (レポート ビルダーおよび SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "データ ソース [Reporting Services], 埋め込み"
  - "データ ソース [Reporting Services], 共有"
ms.assetid: 0e099c7e-8c03-43eb-9ea3-76e52d9ebbe3
caps.latest.revision: 16
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 16
---
# データ ソースの変換 (レポート ビルダーおよび SSRS)
  レポート データ ペインの各データ ソースは、レポートに固有のものとして埋め込まれている場合と、共有されている場合とがあります。 レポート ビルダーにおける共有データ ソースの参照先は、レポート サーバー上または SharePoint サイト上にパブリッシュされた共有データ ソースです。 レポート デザイナーにおける共有データ ソースの参照先は、ソリューション エクスプローラーの **[共有データ ソース]** フォルダーに表示される共有データ ソースです。  
  
 埋め込みデータ ソースと共有データ ソースの相違点の詳細については、「[埋め込みおよび共有のデータ接続またはデータ ソース (レポート ビルダーおよび SSRS)](../Topic/Embedded%20and%20Shared%20Data%20Connections%20or%20Data%20Sources%20\(Report%20Builder%20and%20SSRS\).md)」を参照してください。  
  
 共有データ ソースの作成方法の詳細については、「[埋め込みデータ ソースまたは共有データ ソースを作成する (SSRS)](../Topic/Create%20an%20Embedded%20or%20Shared%20Data%20Source%20\(SSRS\).md)」を参照してください。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## レポート デザイナー  
  
#### 埋め込みデータ ソースから共有データ ソースに変換するには  
  
-   レポート データ ペインでデータ ソースを右クリックし、**[共有データ ソースに変換]** をクリックします。  
  
    > [!NOTE]  
    >  レポート データ ペインが表示されていない場合は、**[表示]** メニューの **[レポート データ]** をクリックします。 ペインがフローティング ウィンドウとして開く場合は、ドッキングすることができます。 詳細については、「[レポート デザイナーのレポート データ ペインをドッキングする (SSRS)](../../reporting-services/tools/dock-the-report-data-pane-in-report-designer-ssrs.md)」を参照してください。  
  
     レポート データ ペインでデータ ソース アイコンが共有データ ソースのアイコンに変わります。 ソリューション エクスプローラーでは、同じ名前の共有データ ソースが **[共有データ ソース]** フォルダーに表示されます。  
  
### 共有データ ソースを埋め込みデータ ソースに変換するには  
  
-   レポート データ ペインでデータ ソースを右クリックし、**[データ ソースのプロパティ]** ダイアログ ボックスを開いて、**[埋め込み接続]** をクリックします。 必要な情報を入力します。  
  
     レポート データ ペインでデータ ソース アイコンが共有データ ソースのアイコンに変わります。  
  
## レポート ビルダー  
  
#### 埋め込みデータ ソースから共有データ ソースに変換するには  
  
-   レポート データ ペインでデータ ソースを右クリックし、**[データ ソースのプロパティ]** ダイアログ ボックスを開いて、**[埋め込み接続]** をクリックします。 必要な情報を入力します。  
  
     レポート データ ペインでデータ ソース アイコンが共有データ ソースのアイコンに変わります。  
  
#### 共有データ ソースを埋め込みデータ ソースに変換するには  
  
-   レポート データ ペインでデータ ソースを右クリックし、**[データ ソースのプロパティ]** ダイアログ ボックスを開いて、**[埋め込み接続]** をクリックします。 必要な情報を入力します。  
  
     レポート データ ペインでデータ ソース アイコンが共有データ ソースのアイコンに変わります。  
  
## 参照  
 [レポート データ ソースを管理する](../../reporting-services/report-data/manage-report-data-sources.md)   
 [データ接続、データ ソース、および接続文字列 (レポート ビルダーおよび SSRS)](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)  
  
  