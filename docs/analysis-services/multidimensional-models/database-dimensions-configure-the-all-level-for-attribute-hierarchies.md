---
title: "属性階層の (All) レベルの構成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- All members
- IsAggregatable property
- topmost levels [Analysis Services]
- (All) levels
- AttributeAllMemberName property
- levels [Analysis Services]
- members [Analysis Services], All
- AllMemberName property
ms.assetid: 0cb35e6f-b10f-483d-b893-78f6ca3979fd
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 46870a942fad5b41d91177772175e9cad43fad0a
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="database-dimensions---configure-the-all-level-for-attribute-hierarchies"></a>データベース ディメンション - 属性階層の (All) レベルを構成します。
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、(All) レベルはシステムによって生成されるオプションのレベルです。 このレベルには 1 つのメンバーが含まれ、その値は直下のレベルに含まれる全メンバーの値の集計です。 このメンバーを All メンバーと呼びます。 All メンバーはシステムによって生成されるメンバーで、ディメンション テーブルには含まれません。 (All) レベルのメンバーは階層の最上位にあるので、このメンバーの値は、階層内の全メンバーの値の集計値です。 通常、All メンバーは階層の既定メンバーとして機能します。  
  
 属性階層に (All) レベルがあるかどうかは属性の **IsAggregatable** プロパティ設定によって決まり、ユーザー定義階層に (All) レベルがあるかどうかはユーザー定義階層の最上位レベルに関する属性の **IsAggregatable** プロパティによって決まります。 **IsAggregatable** プロパティが **True**に設定されている場合は、(All) レベルが存在します。 **IsAggregatable** プロパティが **False**に設定されている場合は、階層に (All) レベルはありません。  
  
## <a name="establishing-the-topmost-level"></a>最上位レベルの設定  
 階層のレベルのソース属性で **IsAggregatable** プロパティが **False** に設定されている場合には、そのレベルより上の階層に集計レベルを表示できません。 非集計レベルは任意の階層の最上位レベルであるか、それより上のレベルのソース属性の **IsAggregatable** プロパティも **False**に設定する必要があります。  
  
## <a name="all-member-and-all-level"></a>All メンバーと (All) レベル  
 (All) レベルの単一のメンバーは、All メンバーと呼ばれます。 ディメンションの **AttributeAllMemberName**プロパティにより、ディメンションの属性の All メンバーの名前が指定されます。 階層の **AllMemberName** プロパティにより、階層の All メンバーの名前が指定されます。  
  
## <a name="see-also"></a>参照  
 [既定のメンバーを定義します。](../../analysis-services/multidimensional-models/attribute-properties-define-a-default-member.md)  
  
  
