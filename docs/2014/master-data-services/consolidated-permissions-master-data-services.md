---
title: 統合アクセス許可 (マスターデータサービス) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [Master Data Services], consolidated member attribute permissions
- consolidated members [Master Data Services], attribute permissions
- permissions [Master Data Services], consolidated members
- members [Master Data Services], consolidated member permissions
ms.assetid: 084055a3-5fd3-43f3-b620-ac6afab42a3d
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 66224262c88176fe0d0ddd1f4291b12213aed928
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66054110"
---
# <a name="consolidated-permissions-master-data-services"></a>統合権限 (Master Data Services)
  統合権限は、エンティティのすべての統合メンバーの属性値に適用されます。  
  
 統合権限は、明示的階層およびコレクションに対して有効なエンティティにのみ適用されます。  
  
 **注記**  
  
-   リーフ権限は、ユーザー インターフェイスの **[エクスプローラー]** 機能領域にのみ適用されます。  
  
-   
  **Name** 属性および **Code** 属性に割り当てられる権限は適用されません。  
  
|権限|[説明]|  
|----------------|-----------------|  
|**読み取り専用**|統合メンバーが表示されますが、ユーザーはそれらのメンバーを追加、削除、または変更できません。|  
|**Update**|統合メンバーが表示され、ユーザーはそれらのメンバーを追加、削除、および変更できます。|  
|**Deny**|エンティティの統合メンバーが表示されません。|  
  
## <a name="attribute-permissions"></a>属性の権限  
 属性の権限は、特定のエンティティの属性の値に適用されます。 属性権限のみを持つユーザーは、メンバーを追加または削除できません。  
  
|権限|[説明]|  
|----------------|-----------------|  
|**読み取り専用**|属性が表示されますが、ユーザーは属性の値を変更できません。|  
|**Update**|属性が表示され、ユーザーは属性の値を変更できます。|  
|**Deny**|属性が表示されません。<br /><br /> 注: Name 属性と Code 属性へのアクセスを明示的に拒否することはできません。|  
  
## <a name="see-also"></a>参照  
 [モデルオブジェクト権限の割り当て &#40;マスターデータサービス&#41;](assign-model-object-permissions-master-data-services.md)   
 [リーフアクセス許可 &#40;マスターデータサービス&#41;](../../2014/master-data-services/leaf-permissions-master-data-services.md)   
 [モデルオブジェクト権限 &#40;マスターデータサービス&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [メンバー &#40;マスターデータサービス&#41;](../../2014/master-data-services/members-master-data-services.md)   
 [属性 &#40;マスターデータサービス&#41;](../../2014/master-data-services/attributes-master-data-services.md)  
  
  
