---
title: 属性階層の (All) レベルの構成 |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 23b00a88c8abf80045a38d0b8cc5d0c695949b0b
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34021679"
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
  
  
