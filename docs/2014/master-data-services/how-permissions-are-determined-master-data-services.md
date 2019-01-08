---
title: アクセス許可の決定方法 (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- permissions [Master Data Services], determining permissions
ms.assetid: 1dc0b43a-d023-4e7d-b027-8b1459fd058c
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 7b138dd1cf07ccfccefb9e1556c743f3c0a45abd
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52747414"
---
# <a name="how-permissions-are-determined-master-data-services"></a>権限の決定方法 (Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]でセキュリティを構成する最も簡単な方法は、ユーザーが属しているグループにモデル オブジェクト権限を割り当てることです。  
  
 次の場合、セキュリティはより複雑になります。  
  
-   モデル オブジェクトと階層メンバーの両方の権限が割り当てられている。  
  
-   ユーザーがグループに属しており、そのユーザーとグループの両方に権限が割り当てられている。  
  
-   ユーザーがグループに属しており、複数のグループに権限が割り当てられている。  
  
## <a name="permissions-assigned-to-a-single-group-or-user"></a>単一のグループまたはユーザーに割り当てられた権限  
 単一のグループまたはユーザーに権限を割り当てた場合、次のワークフローに基づいて権限が決定されます。  
  
 ![mds_conc_security_no_overlap](../../2014/master-data-services/media/mds-conc-security-no-overlap.gif "mds_conc_security_no_overlap")  
  
### <a name="step-1-effective-attribute-permissions-are-determined"></a>手順 1:有効な属性の権限が決定されます。  
 有効な属性の権限は、次のように決定されます。  
  
-   モデル オブジェクトに割り当てられた権限によって、ユーザーがアクセスできる属性が決まる。  
  
-   すべてのモデル オブジェクトは、モデル構造内の上位レベルにある最も近いオブジェクトの権限を自動的に継承する。  
  
-   エンティティと同じレベルのオブジェクトは、暗黙的に拒否される。  
  
-   上位レベルのオブジェクトには、ナビゲーション アクセスが与えられる。 ナビゲーション アクセスの詳細については、次を参照してください。[ナビゲーション アクセス&#40;Master Data Services&#41;](navigational-access-master-data-services.md)します。  
  
 この例で**読み取り専用**エンティティへのアクセス許可が割り当てられているし、そのアクセス許可は、モデル構造内の下位レベルにある属性によって継承されます。 モデルでは、このエンティティとその属性に対するナビゲーション アクセスが提供されています。 モデル内のその他のエンティティは、明示的な権限が割り当てられておらず、権限の継承もしていないため、暗黙的に拒否されます。  
  
 ![mds_conc_inheritance_model](../../2014/master-data-services/media/mds-conc-inheritance-model.gif "mds_conc_inheritance_model")  
  
### <a name="step-2-if-hierarchy-member-permissions-are-assigned-effective-member-permissions-are-determined"></a>手順 2:階層メンバーの権限が割り当てられている場合は、有効なメンバー権限が決定されます。  
 有効な階層メンバーの権限は、次のように決定されます。  
  
-   階層ノードに割り当てられた権限によって、ユーザーがアクセスできるメンバーが決まる。  
  
-   階層内のすべてのノードは、階層構造内の上位レベルにある最も近いオブジェクトの権限を自動的に継承する。  
  
-   同じレベルのノードは、暗黙的に拒否される。  
  
-   権限が割り当てられていない上位レベルのノードは、暗黙的に拒否される。  
  
 この例で**読み取り専用**アクセス許可は、階層の 1 つのノードに割り当てられているし、階層構造内の下位レベルにあるノードによってそのアクセス許可が継承されます。 ルートは、権限が割り当てられていないため、暗黙的に拒否されます。 階層構造内のその他のノードは、明示的な権限が割り当てられておらず、権限の継承もしていないため、暗黙的に拒否されます。  
  
 ![mds_conc_inheritance_hierarchy](../../2014/master-data-services/media/mds-conc-inheritance-hierarchy.gif "mds_conc_inheritance_hierarchy")  
  
### <a name="step-3-the-intersection-of-attribute-and-member-permissions-is-determined"></a>手順 3:属性とメンバーのアクセス許可の積集合が決定されます。  
 有効な属性の権限が有効なメンバーの権限とは異なる場合、個々の属性値ごとに権限を決定する必要があります。 詳細については、「[モデル権限とメンバー権限の重複 (マスター データ サービス)](../../2014/master-data-services/overlapping-model-and-member-permissions-master-data-services.md)」を参照してください。  
  
## <a name="permissions-assigned-to-multiple-groups"></a>複数のグループに割り当てられた権限  
 ユーザーが 1 つ以上のグループに属しており、ユーザーとグループの両方に権限が割り当てられている場合、ワークフローはより複雑になります。  
  
 ![mds_conc_security_group_overlap](../../2014/master-data-services/media/mds-conc-security-group-overlap.gif "mds_conc_security_group_overlap")  
  
 この場合に、モデル オブジェクトと階層メンバーの権限を比較するには、ユーザーとグループでの権限の重複を解決する必要があります。 詳細については、「 [ユーザー権限とグループ権限の重複 (マスター データ サービス)](../../2014/master-data-services/overlapping-user-and-group-permissions-master-data-services.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [ユーザー権限とグループ権限の重複 (マスター データ サービス)](../../2014/master-data-services/overlapping-user-and-group-permissions-master-data-services.md)   
 [モデル権限とメンバー権限の重複 (マスター データ サービス)](../../2014/master-data-services/overlapping-model-and-member-permissions-master-data-services.md)  
  
  
