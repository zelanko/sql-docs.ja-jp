---
title: エンティティ アクセス許可 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- entities [Master Data Services], permissions
- permissions [Master Data Services], entities
ms.assetid: 22785062-4faf-46ee-bffa-01cbd6d5a5b3
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 4219830c82710861ee7b079ce78d1b5859681753
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "65479540"
---
# <a name="entity-permissions-master-data-services"></a>エンティティ権限 (Master Data Services)
  エンティティ権限は、次のものに適用されます。  
  
-   リーフ メンバーと統合メンバーの両方に対する、 **Name** および **Code**を含む、エンティティのすべての属性。  
  
-   エンティティのすべてのコレクション。  
  
-   明示的階層のメンバーシップとリレーションシップ。  
  
 エンティティに対する権限がある場合は、エンティティ、その明示的階層、およびそのコレクションに対してメンバーの追加および削除を行うことができます。  
  
> [!NOTE]  
>  これらの権限は、ユーザー インターフェイスの **[エクスプローラー]** 機能領域にのみ適用されます。  
  
|権限|[説明]|  
|----------------|-----------------|  
|**読み取り専用**|エンティティが表示されますが、ユーザーはメンバーを追加、削除、または変更できません。|  
|**Update**|エンティティが表示され、ユーザーはメンバーを追加、削除、および変更できます。|  
|**Deny**|エンティティが表示されません。|  
  
## <a name="see-also"></a>参照  
 [モデルオブジェクト権限の割り当て &#40;マスターデータサービス&#41;](assign-model-object-permissions-master-data-services.md)   
 [モデルオブジェクト権限 &#40;マスターデータサービス&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [エンティティ &#40;マスターデータサービス&#41;](../../2014/master-data-services/entities-master-data-services.md)  
  
  
