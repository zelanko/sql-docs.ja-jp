---
title: 通知 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- notifications [Master Data Services]
- notifications [Master Data Services], about notifications
- e-mail [Master Data Services]
- e-mail [Master Data Services], about e-mail notifications
ms.assetid: d7ad32d5-9fe5-48fd-8c61-0b00c0aff082
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 54f8cdc55322144414be11dd837bd723b4ed3c10
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "65478969"
---
# <a name="notifications-master-data-services"></a>通知 (Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]ビジネスルールの検証が失敗した場合、またはモデルのバージョンの状態が変更された場合に、電子メール通知を送信するようにを構成できます。  
  
## <a name="how-notifications-are-sent"></a>通知の送信方法  
 
  [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]の通知を構成します。 通知では、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]データベースをホストするのインスタンスでデータベースメールを使用して電子メールメッセージを送信します。 データベース メールの詳細については、 [オンライン ブックの「](../relational-databases/database-mail/database-mail-configuration-objects.md) データベース メール構成オブジェクト [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 」を参照してください。  
  
## <a name="when-notifications-are-sent"></a>通知の送信タイミング  
 通知を構成すると、以降は次のインスタンスで自動の電子メール通知を送信できます。  
  
|インスタンス|[説明]|  
|--------------|-----------------|  
|データがビジネス ルール検証に失敗した場合|属性値がビジネス ルールの検証に失敗した場合に電子メールを送信するように、個々のビジネス ルールを構成する必要があります。 詳細については、「 [通知を送信するようにビジネス ルールを構成する (マスター データ サービス)](configure-business-rules-to-send-notifications-master-data-services.md)の通知を構成します。|  
|モデル バージョンの状態が変わった場合|モデル バージョンの状態が変わるたびに、モデル管理者であるユーザーは自動的に通知を受け取ります。 詳細については、「 [管理者 (マスター データ サービス)](../../2014/master-data-services/administrators-master-data-services.md)にアクセスすることなくグループに対してユーザーの追加または削除を行うことができます。|  
  
## <a name="system-settings"></a>システム設定  
 
  [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] には、通知に影響を与える設定があります。 これらの設定は、 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] で調整するか、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースの System Settings テーブルで直接調整することができます。 詳細については、「[システム設定 &#40;マスター データ サービス&#41;](../../2014/master-data-services/system-settings-master-data-services.md)」を参照してください。  
  
## <a name="related-tasks"></a>Related Tasks  
  
|タスクの説明|トピック|  
|----------------------|-----------|  
|電子メールの通知を送信するように [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] を構成する。|[マスターデータサービス&#41;&#40;電子メール通知を構成する](../../2014/master-data-services/configure-email-notifications-master-data-services.md)|  
|属性値の変更時に通知を送信するように、 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] を構成する。|[通知を送信するようにビジネスルールを構成する &#40;マスターデータサービス&#41;](configure-business-rules-to-send-notifications-master-data-services.md)|  
  
## <a name="related-content"></a>関連コンテンツ  
  
-   [ビジネスルール &#40;マスターデータサービス&#41;](../../2014/master-data-services/business-rules-master-data-services.md)  
  
-   [バージョン &#40;マスターデータサービス&#41;](../../2014/master-data-services/versions-master-data-services.md)  
  
-   [電子メール通知のトラブルシューティング (マスターデータサービス)](https://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-email-notifications-master-data-services.aspx)  
  
  
