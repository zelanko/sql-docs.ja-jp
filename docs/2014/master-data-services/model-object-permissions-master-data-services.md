---
title: モデル オブジェクト アクセス許可 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- permissions [Master Data Services], model objects
- models [Master Data Services], object permissions
ms.assetid: fab6335b-4cae-47de-ae7c-6c4743e0680f
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 754920cac0a832ac5ae1ff8959e710815d68fd70
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84971192"
---
# <a name="model-object-permissions-master-data-services"></a>モデル オブジェクト権限 (Master Data Services)
  モデル オブジェクト権限は必須です。 これにより、UI の **[エクスプローラー]** 機能領域でユーザーがアクセスできる属性が決まります。  
  
 たとえば、ユーザーに Product エンティティに対する **更新** 権限を割り当てると、ユーザーは Product エンティティのすべての属性を更新できます。 単一の属性に対する **更新** 権限を割り当てた場合は、ユーザーはその属性のみを更新できます。  
  
 個別の各属性値に割り当てられるセキュリティを決定するため、モデル オブジェクト権限は階層メンバー権限と組み合わされて、ユーザーがアクセスできるメンバーが決定されます。  
  
 [**エクスプローラー**] 以外の機能領域へのアクセスをユーザーに付与するには、ユーザーがモデル管理者である必要があります。これには、モデルオブジェクト権限の割り当ても含まれます。 詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。  
  
 モデルオブジェクト権限は、 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ユーザーインターフェイス (UI) の [**ユーザー/グループの権限**] 機能領域の [**モデル**] タブで割り当てられます。このタブでは、モデルがツリー構造として表されます。 ツリー内のオブジェクトに権限を割り当てると、下位にあるすべてのオブジェクトがその権限を継承します。 継承をオーバーライドするには、個々のオブジェクトに権限を割り当てます。  
  
 モデルオブジェクトには、**読み取り専用**、**更新**、または**拒否**の権限を割り当てることができます。 **[モデル]** タブで権限を割り当てない場合、ユーザーは [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]でモデルおよびデータを表示できません。  
  
## <a name="best-practice"></a>推奨事項  
 通常は、モデルオブジェクトに**更新**権限を割り当て、その下のオブジェクトに権限を明示的に割り当てる必要があります。 下にあるオブジェクトに権限を割り当てないと、権限が継承されて、ユーザーは管理者になります。  
  
## <a name="see-also"></a>参照  
 [モデルオブジェクト権限の割り当て &#40;マスターデータサービス&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)   
 [モデル権限 &#40;マスターデータサービス&#41;](../../2014/master-data-services/model-permissions-master-data-services.md)   
 [機能領域のアクセス許可 &#40;マスターデータサービス&#41;](../../2014/master-data-services/functional-area-permissions-master-data-services.md)   
 [階層メンバーの権限 &#40;マスターデータサービス&#41;](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md)   
 [権限の決定方法 (マスター データ サービス)](../../2014/master-data-services/how-permissions-are-determined-master-data-services.md)  
  
  
