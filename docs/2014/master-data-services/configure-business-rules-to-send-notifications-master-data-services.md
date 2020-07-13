---
title: 通知を送信するようにビジネス ルールを構成する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], configuring notifications
- e-mail [Master Data Services], configuring business rules
- notifications [Master Data Services], configuring business rules
ms.assetid: b24f7b11-ab53-4642-999c-e17b543b3558
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 33e95706e86ca560741850457d66843bfe6bd652
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84971952"
---
# <a name="configure-business-rules-to-send-notifications-master-data-services"></a>通知を送信するようにビジネス ルールを構成する (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、属性値の変更をユーザーに通知する場合は、通知を送信するようにビジネス ルールを構成します。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   **[システム管理]** および **[ユーザー/グループの権限]** 機能領域にアクセスする権限が必要です。 **[ユーザー/グループの権限]** 機能領域に対する権限がないと、通知を送信するユーザーおよびグループの一覧を表示できません。  
  
-   モデル管理者である必要があります。 詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。  
  
-   検証アクションを使用するビジネス ルールが既に存在している必要があります。 詳細については、「[ビジネス ルールを作成しパブリッシュする (マスター データ サービス)](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md)」を参照してください。  
  
-   通知を受け取るユーザーまたはグループには、検証に失敗した属性に対する **読み取り専用** 以上の権限が必要です。 属性に対する権限が明示的または暗黙的に拒否されるユーザーまたはグループは、電子メールを受け取りますが、 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で属性にアクセスすることはできません。  
  
-   メールがグループに送信された場合は、 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] にアクセスしたグループ メンバーのみが電子メールを受信します。  
  
### <a name="to-configure-business-rules-to-send-notifications"></a>通知を送信するようにビジネス ルールを構成するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。  
  
2.  メニュー バーから **[管理]** をポイントして **[ビジネス ルール]** をクリックします。  
  
3.  **[ビジネス ルールのメンテナンス]** ページの **[モデル]** の一覧からモデルを選択します。  
  
4.  **[エンティティ]** の一覧からエンティティを選択します。  
  
5.  [**メンバーの種類**] ボックスの一覧から、メンバーの種類を選択します。  
  
6.  **[属性]** の一覧で、属性を選択するか、 **[すべて]** の既定値のままにします。  
  
7.  グリッドのビジネスルールの行で、[**通知**] フィールドをダブルクリックします。  
  
8.  サブメニューから、電子メール通知を送信するユーザーまたはグループをクリックします。  
  
## <a name="next-steps"></a>次の手順  
  
-   以下のいずれかの手順でビジネス ルールをデータに適用します。  
  
    -   [ビジネス ルールに対して特定のメンバーを検証する (マスター データ サービス)](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
    -   [ビジネス ルールに対してバージョンを検証する (マスター データ サービス)](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
-   電子メール プロトコルを次のように構成します。  
  
    -   [電子メール通知を構成する (マスター データ サービス)](../../2014/master-data-services/configure-email-notifications-master-data-services.md)  
  
## <a name="see-also"></a>参照  
 [通知 &#40;マスターデータサービス&#41;](../../2014/master-data-services/notifications-master-data-services.md)   
 [電子メール通知を構成する (マスター データ サービス)](../../2014/master-data-services/configure-email-notifications-master-data-services.md)  
  
  
