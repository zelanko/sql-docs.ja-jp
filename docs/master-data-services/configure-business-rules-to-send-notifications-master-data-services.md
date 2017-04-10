---
title: "通知を送信するようにビジネス ルールを構成する (マスター データ サービス) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ビジネス ルール [マスター データ サービス], 通知の構成"
  - "電子メール [マスター データ サービス], ビジネス ルールの構成"
  - "通知 [マスター データ サービス], ビジネス ルールの構成"
ms.assetid: b24f7b11-ab53-4642-999c-e17b543b3558
caps.latest.revision: 10
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 10
---
# 通知を送信するようにビジネス ルールを構成する (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、属性値の変更をユーザーに通知する場合は、通知を送信するようにビジネス ルールを構成します。  
  
## 前提条件  
 この手順を実行するには  
  
-   **[システム管理]** および **[ユーザー/グループの権限]** 機能領域にアクセスする権限が必要です。 **[ユーザー/グループの権限]** 機能領域に対する権限がないと、通知を送信するユーザーおよびグループの一覧を表示できません。  
  
-   モデル管理者である必要があります。 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](../master-data-services/administrators-master-data-services.md)」を参照してください。  
  
-   検証アクションを使用するビジネス ルールが既に存在している必要があります。 詳細については、「[ビジネス ルールを作成しパブリッシュする (マスター データ サービス)](../master-data-services/create-and-publish-a-business-rule-master-data-services.md)」を参照してください。  
  
-   通知を受け取るユーザーまたはグループには、検証に失敗した属性に対する**読み取り専用**以上の権限が必要です。 属性に対する権限が明示的または暗黙的に拒否されるユーザーまたはグループは、電子メールを受け取りますが、 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で属性にアクセスすることはできません。  
  
-   メールがグループに送信された場合は、 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] にアクセスしたグループ メンバーのみが電子メールを受信します。  
  
### 通知を送信するようにビジネス ルールを構成するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]**をクリックします。  
  
2.  メニュー バーから **[管理]** をポイントして **[ビジネス ルール]**をクリックします。  
  
3.  **[ビジネス ルール]** ページの **[モデル]** ボックスの一覧からモデルを選択します。  
  
4.  **[エンティティ]** ドロップダウン リストから、エンティティを選択します。  
  
5.  **[メンバーの種類]** ドロップ ダウン リストから、メンバーの種類を選択します。  
  
6.  グリッドで、編集するビジネス ルールの行を選択し、 **[編集]**をクリックします。  
  
7.  **[通知を送信する]** チェックボックスをオンにし、ドロップダウン リストから、電子メール通知を送信するユーザーまたはグループを選択します。  
  
8.  **[保存]**をクリックします。  
  
9. **[すべてパブリッシュ]**をクリックします。  
  
10. 確認のダイアログ ボックスで **[OK]**をクリックします。 **[ビジネス ルールの状態]** 列の値が **[アクティブ]** に変わり、 **[通知]** 列に通知の送信先ユーザーまたはグループが表示されます。  
  
## 次の手順  
  
-   以下のいずれかの手順でビジネス ルールをデータに適用します。  
  
    -   [ビジネス ルールに対して特定のメンバーを検証する (マスター データ サービス)](../master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
    -   [ビジネス ルールに対してバージョンを検証する (マスター データ サービス)](../master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
-   電子メール プロトコルを次のように構成します。  
  
    -   [電子メール通知を構成する (マスター データ サービス)](../master-data-services/configure-email-notifications-master-data-services.md)  
  
## 参照  
 [通知 (マスター データ サービス)](../master-data-services/notifications-master-data-services.md)   
 [電子メール通知を構成する (マスター データ サービス)](../master-data-services/configure-email-notifications-master-data-services.md)  
  
  