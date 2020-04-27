---
title: Reporting Services サイトコレクションの機能 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e05ae162-a4b2-489d-9853-d6b09414e632
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9475ee323222b800a9c4b9a86e737fdd161e7a60
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66102763"
---
# <a name="reporting-services-site-collection-features"></a>Reporting Services サイト コレクション機能
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint モードには、SharePoint サイト コレクションの 3 つの機能が用意されています。 これらの機能は、一般的な [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint モードのレポート環境、 [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)]、 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Enterprise Edition 用の [!INCLUDE[SPS2010](../includes/sps2010-md.md)] アドインの機能、および SharePoint サーバーの全体管理での [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 用の管理操作をサポートします。  
  
## <a name="site-collection-features"></a>サイト コレクションの機能  
 次の表に、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] のサイト コレクションの機能を示します。  
  
|機能|説明|  
|-------------|-----------------|  
|**レポート サーバーの全体管理機能**|[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] レポート サーバーとの統合を管理する機能を有効にします。 この機能は、SharePoint サーバーの全体管理のサイト コレクション内でのみインストールおよび使用されます。<br /><br /> レポートサーバーの統合機能は、sharepoint 製品用[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]アドインをインストールした後、sharepoint サーバーの全体管理のサイトコレクションで自動的にアクティブ化されます。 場合によっては、この機能を手動でアクティブ化する必要があります。 レポート サーバー機能をアクティブ化するには、SharePoint サーバーの全体管理の [サイトの設定] ページ内の [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ページを使用します。<br /><br /> [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 以降のバージョンの SharePoint 製品用アドインをインストールすると、既存のすべてのサイト コレクションのレポート サーバーの統合機能がアクティブ化されます。 また、この機能は、新しいサイト コレクションに対して自動的にアクティブ化されます。|  
|**レポート サーバーの統合機能**|を使用した[!INCLUDE[msCoName](../includes/msconame-md.md)]リッチレポートを有効にします。[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]<br /><br /> この機能は、既定でアクティブになっています。|  
|**Power View の統合機能**|PowerPivot ブックおよび Analysis Services の表形式のデータベースに対する対話形式のデータ探索と視覚的な表示を有効にします。<br /><br /> この機能には、次のデータ ソースのコンテキスト メニューからアクセスできます。<br /><br /> .rdlx<br /><br /> .rsds<br /><br /> .bism 接続ファイル<br /><br /> <br /><br /> [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] がコンテキスト メニューに表示されない場合は、 **Power View の統合機能** がアクティブになっていることを確認してください。<br /><br /> この機能は、既定で非アクティブになっています。|  
  
## <a name="see-also"></a>参照  
 [SharePoint でのレポートサーバーと Power View の統合機能のアクティブ化](activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)   
 [SharePoint モード&#40;のサイト設定とサイト機能の Reporting Services&#41;](../../2014/reporting-services/reporting-services-site-settings-and-site-features-sharepoint-mode.md)   
 [SharePoint サーバーの全体管理でレポート サーバーのファイル同期機能をアクティブにする](../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md)  
  
  
