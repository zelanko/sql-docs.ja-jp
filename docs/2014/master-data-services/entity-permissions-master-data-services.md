---
title: エンティティ アクセス許可 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- entities [Master Data Services], permissions
- permissions [Master Data Services], entities
ms.assetid: 22785062-4faf-46ee-bffa-01cbd6d5a5b3
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: c27e757bc7e24434611b809ae884f9a243d83c2a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36082790"
---
# <a name="entity-permissions-master-data-services"></a>エンティティ権限 (Master Data Services)
  エンティティ権限は、次のものに適用されます。  
  
-   リーフ メンバーと統合メンバーの両方に対する、 **Name** および **Code**を含む、エンティティのすべての属性。  
  
-   エンティティのすべてのコレクション。  
  
-   明示的階層のメンバーシップとリレーションシップ。  
  
 エンティティに対する権限がある場合は、エンティティ、その明示的階層、およびそのコレクションに対してメンバーの追加および削除を行うことができます。  
  
> [!NOTE]  
>  これらの権限は、ユーザー インターフェイスの **[エクスプローラー]** 機能領域にのみ適用されます。  
  
|権限|説明|  
|----------------|-----------------|  
|**読み取り専用です。**|エンティティが表示されますが、ユーザーはメンバーを追加、削除、または変更できません。|  
|**Update**|エンティティが表示され、ユーザーはメンバーを追加、削除、および変更できます。|  
|**Deny**|エンティティが表示されません。|  
  
## <a name="see-also"></a>参照  
 [モデル オブジェクト権限を割り当てる&#40;マスター データ サービス&#41;](assign-model-object-permissions-master-data-services.md)   
 [モデル オブジェクト権限&#40;マスター データ サービス&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [エンティティ (マスター データ サービス)](../../2014/master-data-services/entities-master-data-services.md)  
  
  