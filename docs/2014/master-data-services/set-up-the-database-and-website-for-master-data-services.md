---
title: マスターデータサービス | のデータベースと Web サイトを設定します。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
f1_keywords:
- sql12.mds.configmanager.general.f1
ms.assetid: d50863e7-50d9-4ab8-aabb-fd68e2d132a1
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d359084d1db778029046f925c630b001bb820f6b
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84971092"
---
# <a name="set-up-the-database-and-website-for-master-data-services"></a>マスター データ サービスのデータベースと Web サイトの設定
  [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] を使って、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] のデータベースと Web サイトを設定する (MDS)  
  
 データベースと Web サイトを設定するには、次のタスクを実行してください。  
  
1.  **の** [データベース構成] [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]ページで、データベースを作成します。  
  
     詳細については、「データベースの構成」ページを参照して[&#40;マスターデータサービス構成マネージャー&#41;](../../2014/master-data-services/database-configuration-page-master-data-services-configuration-manager.md)と[データベースの作成ウィザード &#40;マスターデータサービス構成マネージャー ](../../2014/master-data-services/create-database-wizard-master-data-services-configuration-manager.md)&#41;を参照してください。  
  
2.  **の** [Web 構成] [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]ページで、新しい Web サイトを作成するか、既定の Web サイトを選ぶか、別の既存の Web サイトを選びます。 その後、MDS データベースを、選んだ Web アプリケーションや作成した Web アプリケーションに関連付けます。  
  
     詳細については、「 [Web 構成ページ &#40;マスターデータサービス構成マネージャー&#41;](../../2014/master-data-services/web-configuration-page-master-data-services-configuration-manager.md) 」と「web[サイトの作成] ダイアログボックス &#40;マスターデータサービス構成マネージャー ](../../2014/master-data-services/create-website-dialog-box-master-data-services-configuration-manager.md)&#41;」を参照してください。  
  
3.  (省略可能) **の** [Web 構成] [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]ページで、Data Quality Services との統合を有効にします。  
  
     詳細については、「 [Web 構成ページ &#40;マスターデータサービス構成マネージャー&#41;](../../2014/master-data-services/web-configuration-page-master-data-services-configuration-manager.md) 」と「[マスターデータサービスと Data Quality Services の統合を有効にする](install-windows/enable-data-quality-services-integration-with-master-data-services.md)」を参照してください。  
  
 また、 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] を使って、MDS データベースに関連付けられている Web アプリケーションとサービスの設定値を指定できます。 たとえば、データの読み込み頻度や検証メールの送信頻度を指定できます。 詳細については、「[システム設定 &#40;マスター データ サービス&#41;](../../2014/master-data-services/system-settings-master-data-services.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [マスターデータサービスデータベース](../../2014/master-data-services/master-data-services-database.md)   
 [マスター データ マネージャー Web アプリケーション](../../2014/master-data-services/master-data-manager-web-application.md)  
  
  
