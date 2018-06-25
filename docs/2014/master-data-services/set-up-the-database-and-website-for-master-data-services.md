---
title: マスター データ サービスのデータベースと web サイトを設定 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.mds.configmanager.general.f1
ms.assetid: d50863e7-50d9-4ab8-aabb-fd68e2d132a1
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 09e3e92d20182be2feb1c357cc1d3f518c55e5ad
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36166089"
---
# <a name="set-up-the-database-and-website-for-master-data-services"></a>マスター データ サービスのデータベースと Web サイトの設定
  使用して、[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]データベースとの web サイトを設定する[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)](MDS)  
  
 データベースと Web サイトを設定するには、次のタスクを実行してください。  
  
1.  使用してデータベースを作成、**データベース構成**ページ[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]です。  
  
     詳細については、次を参照してください[データベース構成 ページ&#40;Master Data Services 構成マネージャー&#41; ](../../2014/master-data-services/database-configuration-page-master-data-services-configuration-manager.md)と[データベースの作成ウィザード&#40;Master Data Services 構成マネージャー&#41; 。](../../2014/master-data-services/create-database-wizard-master-data-services-configuration-manager.md).  
  
2.  新しい web サイトの作成を既定の web サイトを選択するか既存の別の web サイトの選択を使用して、 **Web 構成**ページに[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]です。 その後、MDS データベースを、選んだ Web アプリケーションや作成した Web アプリケーションに関連付けます。  
  
     詳細については、次を参照してください[Web 構成 ページ&#40;Master Data Services 構成マネージャー&#41; ](../../2014/master-data-services/web-configuration-page-master-data-services-configuration-manager.md)と[web サイト ダイアログ ボックスの作成&#40;Master Data Services 構成マネージャー&#41; 。](../../2014/master-data-services/create-website-dialog-box-master-data-services-configuration-manager.md).  
  
3.  (省略可能)Data Quality Services を使用するとの統合を有効にする、 **Web 構成**ページ[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]です。  
  
     詳細については、次を参照してください。 [Web 構成 ページ&#40;Master Data Services 構成マネージャー&#41; ](../../2014/master-data-services/web-configuration-page-master-data-services-configuration-manager.md)と[Enable Data Quality Services Integration with Master Data Services](install-windows/enable-data-quality-services-integration-with-master-data-services.md)です。  
  
 使用することも[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]web アプリケーションと、MDS データベースに関連付けられているサービスの設定を指定します。 たとえば、データの読み込み頻度や検証メールの送信頻度を指定できます。 詳細については、「[システム設定 &#40;マスター データ サービス&#41;](../../2014/master-data-services/system-settings-master-data-services.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [マスター データ サービス データベース](../../2014/master-data-services/master-data-services-database.md)   
 [マスター データ マネージャー Web アプリケーション](../../2014/master-data-services/master-data-manager-web-application.md)  
  
  