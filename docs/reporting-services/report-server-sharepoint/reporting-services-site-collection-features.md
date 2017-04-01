---
title: "Reporting Services サイト コレクション機能 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e05ae162-a4b2-489d-9853-d6b09414e632
caps.latest.revision: 8
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# Reporting Services サイト コレクション機能
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モードには、SharePoint サイト コレクションの 3 つの機能が用意されています。 これらの機能は、一般的な [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モードのレポート環境、[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]、[!INCLUDE[SPS2010](../../includes/sps2010-md.md)] Enterprise Edition 用の [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインの機能、および SharePoint サーバーの全体管理での [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 用の管理操作をサポートします。  
  
## サイト コレクションの機能  
 次の表に、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のサイト コレクションの機能を示します。  
  
|機能|Description|  
|-------------|-----------------|  
|**レポート サーバーの全体管理機能**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバーとの統合を管理する機能を有効にします。 この機能は、SharePoint サーバーの全体管理のサイト コレクション内でのみインストールおよび使用されます。<br /><br /> レポート サーバーの統合機能は、SharePoint 製品用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] アドインをインストールすると自動的に SharePoint サーバーの全体管理のサイト コレクションでアクティブ化されます。 場合によっては、この機能を手動でアクティブ化する必要があります。 レポート サーバー機能をアクティブ化するには、SharePoint サーバーの全体管理の [サイトの設定] ページ内の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ページを使用します。<br /><br /> [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 以降のバージョンの SharePoint 製品用アドインをインストールすると、既存のすべてのサイト コレクションのレポート サーバーの統合機能がアクティブ化されます。 また、この機能は、新しいサイト コレクションに対して自動的にアクティブ化されます。|  
|**レポート サーバーの統合機能**|次のものを使用して、豊富なレポート機能を有効にします。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]<br /><br /> この機能は、既定でアクティブになっています。|  
|**Power View の統合機能**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックおよび Analysis Services の表形式のデータベースに対する対話形式のデータ探索と視覚的な表示を有効にします。<br /><br /> この機能には、次のデータ ソースのコンテキスト メニューからアクセスできます。<br /><br /> **.rdlx**<br /><br /> **.rsds**<br /><br /> **.bism** 接続ファイル<br /><br /> <br /><br /> [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] がコンテキスト メニューに表示されない場合は、**Power View の統合機能**がアクティブになっていることを確認してください。<br /><br /> この機能は、既定で非アクティブになっています。|  
  
## 参照  
 [SharePoint でのレポート サーバーと Power View の統合機能のアクティブ化](../../reporting-services/report-server-sharepoint/activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)   
 [Reporting Services のサイト設定とサイト機能 &#40;SharePoint モード&#41;](../../reporting-services/report-server-sharepoint/reporting-services-site-settings-and-site-features-sharepoint-mode.md)   
 [SharePoint サーバーの全体管理でレポート サーバーのファイル同期機能をアクティブにする](../../reporting-services/report-server-sharepoint/activate-the-report-server-file-sync-feature-in-sharepoint-ca.md)  
  
  