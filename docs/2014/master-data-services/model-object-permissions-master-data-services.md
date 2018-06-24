---
title: モデル オブジェクト アクセス許可 (Master Data Services) | Microsoft Docs
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
- permissions [Master Data Services], model objects
- models [Master Data Services], object permissions
ms.assetid: fab6335b-4cae-47de-ae7c-6c4743e0680f
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: e0e6e04de7c7ed4a483585e6a4228682f0e3a354
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36070735"
---
# <a name="model-object-permissions-master-data-services"></a>モデル オブジェクト権限 (Master Data Services)
  モデル オブジェクト権限は必須です。 これにより、UI の **[エクスプローラー]** 機能領域でユーザーがアクセスできる属性が決まります。  
  
 たとえば、ユーザーに Product エンティティに対する **更新** 権限を割り当てると、ユーザーは Product エンティティのすべての属性を更新できます。 単一の属性に対する **更新** 権限を割り当てた場合は、ユーザーはその属性のみを更新できます。  
  
 個別の各属性値に割り当てられるセキュリティを決定するため、モデル オブジェクト権限は階層メンバー権限と組み合わされて、ユーザーがアクセスできるメンバーが決定されます。  
  
 以外の機能領域へのユーザー アクセスを許可する**エクスプ ローラー**、モデル オブジェクト権限の割り当ても含まれますモデル管理者である必要があります。 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](administrators-master-data-services.md)」を参照してください。  
  
 モデル オブジェクト権限は、[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]のユーザー インターフェイス (UI) を使用して、**[ユーザー/グループの権限]** 機能領域の **[モデル]** タブで割り当てられます。このタブでは、モデルがツリー構造として表されます。 ツリー内のオブジェクトに権限を割り当てると、下位にあるすべてのオブジェクトがその権限を継承します。 継承をオーバーライドするには、個々のオブジェクトに権限を割り当てます。  
  
 割り当てることができます**読み取り専用**、**更新**、または**Deny**モデル オブジェクトに対する権限。 **[モデル]** タブで権限を割り当てない場合、ユーザーは [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]でモデルおよびデータを表示できません。  
  
## <a name="best-practice"></a>推奨事項  
 一般に、割り当てる必要があります**更新**モデル オブジェクトに対する権限下にあるオブジェクトに権限を明示的に割り当てるとします。 下にあるオブジェクトに権限を割り当てないと、権限が継承されて、ユーザーは管理者になります。  
  
## <a name="see-also"></a>参照  
 [モデル オブジェクト権限を割り当てる&#40;マスター データ サービス&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)   
 [モデル アクセス許可 (マスター データ サービス)](../../2014/master-data-services/model-permissions-master-data-services.md)   
 [機能領域アクセス許可 (マスター データ サービス)](../../2014/master-data-services/functional-area-permissions-master-data-services.md)   
 [階層メンバーの権限&#40;マスター データ サービス&#41;](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md)   
 [権限の決定方法&#40;マスター データ サービス&#41;](../../2014/master-data-services/how-permissions-are-determined-master-data-services.md)  
  
  