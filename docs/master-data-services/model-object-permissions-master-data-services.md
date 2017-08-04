---
title: "モデル オブジェクト権限 (Master Data Services) |Microsoft ドキュメント"
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
- permissions [Master Data Services], model objects
- models [Master Data Services], object permissions
ms.assetid: fab6335b-4cae-47de-ae7c-6c4743e0680f
caps.latest.revision: 9
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ee6ede91067d2b358a403458e07af37b2f895ac3
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="model-object-permissions-master-data-services"></a>モデル オブジェクト権限 (Master Data Services)
  モデル オブジェクト権限は必須です。 これにより、UI の **[エクスプローラー]** 機能領域でユーザーがアクセスできる属性が決まります。  
  
 たとえば、ユーザーに Product エンティティに対する **更新** 権限を割り当てると、ユーザーは Product エンティティのすべての属性を更新できます。 単一の属性に対する **更新** 権限を割り当てた場合は、ユーザーはその属性のみを更新できます。  
  
 個別の各属性値に割り当てられるセキュリティを決定するため、モデル オブジェクト権限は階層メンバー権限と組み合わされて、ユーザーがアクセスできるメンバーが決定されます。  
  
 **[エクスプローラー]** 以外の機能領域へのアクセス権限をユーザーに付与するには、ユーザーはモデル管理者である必要があります。これには、オブジェクト モデルでの管理権限の割り当ても含まれます。 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](../master-data-services/administrators-master-data-services.md)」を参照してください。  
  
 モデル オブジェクト権限は、[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]のユーザー インターフェイス (UI) を使用して、**[ユーザー/グループの権限]** 機能領域の **[モデル]** タブで割り当てられます。 このタブでは、モデルがツリー構造として表されます。 ツリー内のオブジェクトに権限を割り当てると、下位にあるすべてのオブジェクトがその権限を継承します。 継承を無効にするには、個々のオブジェクトに権限を割り当てます。  
  
 読み取り、作成、更新、削除、拒否などの権限を組み合わせてモデル オブジェクトに割り当てることができます。 **[モデル]** タブで権限を割り当てない場合、ユーザーは [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]でモデルおよびデータを表示できません。  
  
## <a name="best-practice"></a>推奨事項  
 一般に、 **すべての** 権限をモデル オブジェクトに割り当てた後、その下にあるオブジェクトに権限を明示的に割り当てる必要があります。  
  
## <a name="external-resources"></a>外部リソース  
 msdn.com のブログ投稿「 [Security Improvements (セキュリティの向上)](http://go.microsoft.com/fwlink/p/?LinkId=615376)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [モデル オブジェクト権限を割り当てる & #40 です。マスター データ サービス &#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [モデル権限 & #40 です。マスター データ サービス &#41;](../master-data-services/model-permissions-master-data-services.md)   
 [機能領域権限 & #40 です。マスター データ サービス &#41;](../master-data-services/functional-area-permissions-master-data-services.md)   
 [階層メンバーの権限 & #40 です。マスター データ サービス &#41;](../master-data-services/hierarchy-member-permissions-master-data-services.md)   
 [アクセス許可を決定する方法 (&) #40 です。マスター データ サービス &#41;](../master-data-services/how-permissions-are-determined-master-data-services.md)  
  
  
