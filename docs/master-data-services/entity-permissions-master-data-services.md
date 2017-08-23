---
title: "エンティティ権限 (Master Data Services) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- entities [Master Data Services], permissions
- permissions [Master Data Services], entities
ms.assetid: 22785062-4faf-46ee-bffa-01cbd6d5a5b3
caps.latest.revision: 6
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 981c150415bed3470b33c29d34ab8e30e0dbf37e
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="entity-permissions-master-data-services"></a>エンティティ権限 (Master Data Services)
  エンティティ権限は、次のものに適用されます。  
  
-   リーフ メンバーと統合メンバーの両方に対する、 **Name** および **Code**を含む、エンティティのすべての属性。  
  
-   エンティティのすべてのコレクション。  
  
-   明示的階層のメンバーシップとリレーションシップ。  
  
 エンティティに対する権限がある場合は、エンティティ、その明示的階層、およびそのコレクションに対してメンバーの追加および削除を行うことができます。  
  
> [!NOTE]  
>  これらの権限は、ユーザー インターフェイスの **[エクスプローラー]** 機能領域にのみ適用されます。  
  
|権限|Description|  
|----------------|-----------------|  
|**読み取り**|ユーザーは、メンバー、属性、階層メンバーシップ、コレクション メンバーシップを読み取ることができます。|  
|**作成**|ユーザーはメンバーを作成し、作成時に属性値を割り当てることができます。|  
|**Update**|ユーザーは、メンバー、属性、階層メンバーシップ、コレクション メンバーシップを更新できます。|  
|**Del**|ユーザーはメンバーを削除できます。|  
|**Deny**|エンティティに対するすべてのアクセスを拒否します。|  
  
 読み取り、作成、更新、削除の各権限は組み合わせることができます。 作成、更新、削除の各権限を割り当てた場合は、読み取り権限が自動的に割り当てられます。  
  
## <a name="see-also"></a>参照  
 [モデル オブジェクト権限を割り当てる & #40 です。マスター データ サービス &#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [モデル オブジェクト権限 & #40 です。マスター データ サービス &#41;](../master-data-services/model-object-permissions-master-data-services.md)   
 [エンティティ (マスター データ サービス)](../master-data-services/entities-master-data-services.md)  
  
  
