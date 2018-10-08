---
title: マスター データ サービスのデータベースと web サイトのセットアップ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
f1_keywords:
- sql12.mds.configmanager.general.f1
ms.assetid: d50863e7-50d9-4ab8-aabb-fd68e2d132a1
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 158b1931a9862b8fa419479f024db0bfdbf80cbf
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48205032"
---
# <a name="set-up-the-database-and-website-for-master-data-services"></a>マスター データ サービスのデータベースと Web サイトの設定
  使用して、[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]データベースと web サイトを設定する[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)](MDS)  
  
 データベースと Web サイトを設定するには、次のタスクを実行してください。  
  
1.  使用してデータベースを作成、**データベース構成**ページ[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]します。  
  
     詳しくは、次を参照してください[データベース構成 ページ&#40;Master Data Services 構成マネージャー&#41; ](../../2014/master-data-services/database-configuration-page-master-data-services-configuration-manager.md)と[データベース生成ウィザード&#40;Master Data Services 構成マネージャー&#41; 。](../../2014/master-data-services/create-database-wizard-master-data-services-configuration-manager.md).  
  
2.  新しい web サイトを作成する既定の web サイトを選択するか既存の別の web サイトを選択を使用して、 **Web 構成**ページ[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]します。 その後、MDS データベースを、選んだ Web アプリケーションや作成した Web アプリケーションに関連付けます。  
  
     詳しくは、次を参照してください[Web 構成 ページ&#40;Master Data Services 構成マネージャー&#41; ](../../2014/master-data-services/web-configuration-page-master-data-services-configuration-manager.md)と[web サイトの作成 ダイアログ ボックス&#40;Master Data Services 構成マネージャー&#41; 。](../../2014/master-data-services/create-website-dialog-box-master-data-services-configuration-manager.md).  
  
3.  (省略可能)Data Quality Services との統合を有効にする、 **Web 構成**ページ[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]します。  
  
     詳細については、次を参照してください。 [Web 構成 ページ&#40;Master Data Services 構成マネージャー&#41; ](../../2014/master-data-services/web-configuration-page-master-data-services-configuration-manager.md)と[マスター データ サービスと Data Quality Services 統合を有効にする](install-windows/enable-data-quality-services-integration-with-master-data-services.md)します。  
  
 使用することも[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]web アプリケーションと、MDS データベースに関連付けられているサービスの設定を指定します。 たとえば、データの読み込み頻度や検証メールの送信頻度を指定できます。 詳細については、「[システム設定 &#40;マスター データ サービス&#41;](../../2014/master-data-services/system-settings-master-data-services.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [マスター データ サービス データベース](../../2014/master-data-services/master-data-services-database.md)   
 [マスター データ マネージャー Web アプリケーション](../../2014/master-data-services/master-data-manager-web-application.md)  
  
  
