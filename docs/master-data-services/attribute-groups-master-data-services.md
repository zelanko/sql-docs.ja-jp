---
title: "属性グループ (マスター データ サービス) | Microsoft Docs"
ms.custom: ""
ms.date: "03/15/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "属性グループ [マスター データ サービス]"
  - "属性グループ [マスター データ サービス], 属性グループについて"
ms.assetid: 648b3d0b-e15a-45f9-8292-3a54a072e62c
caps.latest.revision: 10
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 9
---
# 属性グループ (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] では、属性グループがエンティティ内の属性の整理に役立ちます。 エンティティ内に多数の属性がある場合、属性グループを使用すると、[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web アプリケーションでのエンティティの表示が見やすくなります。  
  
## 属性グループによる表示の変更  
 属性グループは、[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] の **[エクスプローラー]** 機能領域のグリッドの上部にタブとして表示されます。  
  
 1 つのエンティティに多くの属性がある場合、**[エクスプローラー]** のグリッド内でエンティティのすべての属性を表示するには、右にスクロールする必要があります。 このスクロールを回避するために、属性グループを作成できます。  
  
-   属性グループには必ず、Name 属性と Code 属性が含まれます。  
  
-   エンティティの各属性は、1 つまたは複数の属性グループに属する場合があります。  
  
-   すべての属性が、**エクスプローラー**の **[すべての属性]** タブに自動的に表示されます。  
  
-   **[すべての属性]** タブを非表示にすることはできません。  
  
 属性グループは、[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] の **[システム管理]** 機能領域で管理します。  
  
## 属性グループの表示と非表示  
 属性グループを作成すると、作成者以外のすべてのユーザーに対して自動的に非表示に設定されます。 グループを表示する方法の詳細については、「[属性グループのユーザーへの表示 (マスター データ サービス)](../master-data-services/make-an-attribute-group-visible-to-users-master-data-services.md)」を参照してください。  
  
 グループ内の特定の属性を非表示にするために、その属性に **[拒否]** の権限を割り当てることができます。 詳細については、「[リーフ権限 (マスター データ サービス)](../master-data-services/leaf-permissions-master-data-services.md)」または「[統合権限 (マスター データ サービス)](../Topic/Consolidated%20Permissions%20\(Master%20Data%20Services\).md)」を参照してください。  
  
## 関連タスク  
  
|タスクの説明|トピック|  
|----------------------|-----------|  
|新しい属性グループを作成して属性を追加する。|[属性グループを作成する (マスター データ サービス)](../master-data-services/create-an-attribute-group-master-data-services.md)|  
|属性グループがユーザーに表示されるようにする。|[属性グループのユーザーへの表示 (マスター データ サービス)](../master-data-services/make-an-attribute-group-visible-to-users-master-data-services.md)|  
|既存の属性グループの名前を変更する。|[属性グループ名を変更する (マスター データ サービス)](../master-data-services/change-an-attribute-group-name-master-data-services.md)|  
|既存の属性グループを削除する。|[属性グループを削除する (マスター データ サービス)](../master-data-services/delete-an-attribute-group-master-data-services.md)|  
  
## 関連コンテンツ  
  
-   [属性 (マスター データ サービス)](../master-data-services/attributes-master-data-services.md)  
  
  