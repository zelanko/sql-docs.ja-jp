---
title: "Reporting Services のサイト コレクション機能 |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/25/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: ea362cd05de5d1ba17ca717d94354d5786119bab
ms.openlocfilehash: 7c86f9ecdbbf4955ba224e40c245fc412742fc30
ms.contentlocale: ja-jp
ms.lasthandoff: 10/06/2017

---
# <a name="reporting-services-site-collection-features"></a>Reporting Services のサイト コレクション機能

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

Reporting Services SharePoint モードでは、次の 3 つの SharePoint サイト コレクション機能を提供します。 機能は、サポート、一般的な Reporting Services SharePoint モードのレポート環境、 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]、SQL Server 2016 Reporting Services アドイン、および SharePoint サーバーの全体管理の Reporting Services 用の管理操作の機能です。

> [!NOTE]
> SQL Server 2016 より後に、SharePoint と reporting Services の統合を使用できなくします。
  
## <a name="site-collection-features"></a>サイト コレクション機能

 次の表では、Reporting Services サイト コレクションの機能について説明します。  
  
|機能|Description|  
|-------------|-----------------|  
|**レポート サーバーの全体管理機能**|Reporting Services レポート サーバーとの統合を管理するための機能を有効にします。 この機能は、SharePoint サーバーの全体管理のサイト コレクション内でのみインストールおよび使用されます。<br /><br /> レポート サーバーの統合機能は、SharePoint 製品用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] アドインをインストールすると自動的に SharePoint サーバーの全体管理のサイト コレクションでアクティブ化されます。 一部の状況では、機能を手動でアクティブ化する必要があります。 レポート サーバーの機能をアクティブ化するには、SharePoint サーバーの全体管理のサイト設定 ページで Reporting Services のページを使用します。<br /><br /> [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Reporting Services のバージョンと後で SharePoint 用アドインの製品アクティブ化すべての既存のサイト コレクションのレポート サーバーの統合機能にアドインがインストールされているときにします。 さらに、機能は自動的に新しいサイト コレクションに対してアクティブです。|  
|**レポート サーバーの統合機能**|により、機能豊富なレポートを使用して[!INCLUDE[msCoName](../../includes/msconame-md.md)]Reporting Services<br /><br /> この機能は、既定でアクティブになっています。|  
|**Power View の統合機能**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックおよび Analysis Services の表形式のデータベースに対する対話形式のデータ探索と視覚的な表示を有効にします。<br /><br /> この機能には、次のデータ ソースのコンテキスト メニューからアクセスできます。<br /><br /> **.rdlx**<br /><br /> **.rsds**<br /><br /> **.bism** 接続ファイル<br /><br /> <br /><br /> [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] がコンテキスト メニューに表示されない場合は、 **Power View の統合機能** がアクティブになっていることを確認してください。<br /><br /> この機能は、既定で非アクティブになっています。|  

## <a name="next-steps"></a>次の手順

[SharePoint でのレポート サーバーと Power View の統合機能のアクティブ化](../../reporting-services/report-server-sharepoint/site-collection-features-report-server-and-power-view.md)   
[Reporting Services のサイト設定とサイト機能 &#40;SharePoint モード&#41;](../../reporting-services/report-server-sharepoint/site-settings-and-features-reporting-services.md)   
[SharePoint サーバーの全体管理でレポート サーバーのファイル同期機能をアクティブにする](../../reporting-services/report-server-sharepoint/activate-the-report-server-file-sync-feature-in-sharepoint-ca.md)  

その他の質問 [Reporting Services のフォーラムに質問してみてください](http://go.microsoft.com/fwlink/?LinkId=620231)
