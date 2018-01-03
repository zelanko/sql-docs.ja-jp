---
title: "ビジネス ルールを削除する (マスター データ サービス) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: non-specific
ms.reviewer: 
ms.suite: sql
ms.technology: master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deleting business rules [Master Data Services]
- business rules [Master Data Services], deleting
ms.assetid: b97aa4f9-569f-451d-ad62-65b81f980299
caps.latest.revision: "7"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 32365e66adee63c6bce756bd6081664776c29ad9
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="delete-a-business-rule-master-data-services"></a>ビジネス ルールを削除する (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、不要になったビジネス ルールを削除します。  
  
> [!NOTE]  
>  ビジネス ルールに対するデータの検証が行われないようにするには、ビジネス ルールを削除する代わりに除外することができます。 詳細については、「 [ビジネス ルールを除外する (マスター データ サービス)](../master-data-services/exclude-a-business-rule-master-data-services.md)」を参照してください。  
  
## <a name="prerequisites"></a>Prerequisites  
 この手順を実行するには  
  
-   **[システム管理]** 機能領域にアクセスする権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「 [管理者 (マスター データ サービス)](../master-data-services/administrators-master-data-services.md)にアクセスすることなくグループに対してユーザーの追加または削除を行うことができます。  
  
### <a name="to-delete-a-business-rule"></a>ビジネス ルールを削除するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]**をクリックします。  
  
2.  メニュー バーから **[管理]** をポイントして **[ビジネス ルール]**をクリックします。  
  
3.  **[ビジネス ルール]** ページの **[モデル]** ドロップダウン リストから、モデルを選択します。  
  
4.  **[エンティティ]** ドロップダウン リストから、エンティティを選択します。  
  
5.  **[メンバーの種類]** ドロップダウン リストから、適用するビジネス ルールのメンバーの種類を選択します。  
  
6.  グリッドで、削除するビジネス ルールの行をクリックします。  
  
7.  **[削除]**をクリックします。  
  
8.  確認のダイアログ ボックスで **[OK]**をクリックします。 **[ビジネス ルールの状態]** 列の値は **[削除の保留中]**です。  
  
9. **[すべてパブリッシュ]**をクリックします。  
  
10. 確認のダイアログ ボックスで **[OK]**をクリックします。 削除されたビジネス ルールはグリッドに表示されなくなります。  
  
## <a name="see-also"></a>参照  
 [ビジネス ルールを除外する (マスター データ サービス)](../master-data-services/exclude-a-business-rule-master-data-services.md)   
 [ビジネス ルールを作成しパブリッシュする (マスター データ サービス)](../master-data-services/create-and-publish-a-business-rule-master-data-services.md)   
 [ビジネス ルール (マスター データ サービス)](../master-data-services/business-rules-master-data-services.md)  
  
  
