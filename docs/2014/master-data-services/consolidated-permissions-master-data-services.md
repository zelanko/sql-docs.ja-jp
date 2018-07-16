---
title: 統合権限 (マスター データ サービス) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- attributes [Master Data Services], consolidated member attribute permissions
- consolidated members [Master Data Services], attribute permissions
- permissions [Master Data Services], consolidated members
- members [Master Data Services], consolidated member permissions
ms.assetid: 084055a3-5fd3-43f3-b620-ac6afab42a3d
caps.latest.revision: 6
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 45b5b6ac268dda2d0462c1a4ada895efe8f90171
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37283438"
---
# <a name="consolidated-permissions-master-data-services"></a>統合権限 (Master Data Services)
  統合権限は、エンティティのすべての統合メンバーの属性値に適用されます。  
  
 統合権限は、明示的階層およびコレクションに対して有効なエンティティにのみ適用されます。  
  
 **注**  
  
-   リーフ権限は、ユーザー インターフェイスの **[エクスプローラー]** 機能領域にのみ適用されます。  
  
-   **Name** 属性および **Code** 属性に割り当てられる権限は適用されません。  
  
|権限|説明|  
|----------------|-----------------|  
|**読み取り専用です。**|統合メンバーが表示されますが、ユーザーはそれらのメンバーを追加、削除、または変更できません。|  
|**Update**|統合メンバーが表示され、ユーザーはそれらのメンバーを追加、削除、および変更できます。|  
|**Deny**|エンティティの統合メンバーが表示されません。|  
  
## <a name="attribute-permissions"></a>属性の権限  
 属性の権限は、特定のエンティティの属性の値に適用されます。 属性の権限のみを持つユーザーは、追加またはメンバーを削除することはできません。  
  
|権限|説明|  
|----------------|-----------------|  
|**読み取り専用です。**|属性が表示されますが、ユーザーは属性の値を変更できません。|  
|**Update**|属性が表示され、ユーザーは属性の値を変更できます。|  
|**Deny**|属性が表示されません。<br /><br /> 注: Name 属性と Code 属性へのアクセスを明示的に拒否することはできません。|  
  
## <a name="see-also"></a>参照  
 [モデル オブジェクト権限を割り当てる&#40;マスター データ サービス&#41;](assign-model-object-permissions-master-data-services.md)   
 [リーフ アクセス許可&#40;マスター データ サービス&#41;](../../2014/master-data-services/leaf-permissions-master-data-services.md)   
 [モデル オブジェクト権限&#40;マスター データ サービス&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [メンバー (マスター データ サービス)](../../2014/master-data-services/members-master-data-services.md)   
 [属性&#40;マスター データ サービス&#41;](../../2014/master-data-services/attributes-master-data-services.md)  
  
  
