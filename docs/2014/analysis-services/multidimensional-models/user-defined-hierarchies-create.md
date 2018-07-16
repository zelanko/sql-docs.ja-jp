---
title: ユーザー定義階層の作成 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- user-defined hierarchies [Analysis Services]
ms.assetid: 16715b85-0630-4a8e-99b0-c0d213cade26
caps.latest.revision: 21
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0521dfa594668d4133cb3c64de539024e2f49c6c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37289758"
---
# <a name="create-user-defined-hierarchies"></a>ユーザー定義階層の作成
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] を使用すると、ユーザー定義階層を作成できます。 階層とは、属性に基づいたレベルのコレクションのことです。 たとえば、時間階層には、年、四半期、月、週、および日の各レベルが含まれる場合があります。 階層によっては、各メンバー属性が、その上位にあるメンバー属性を一意に示すことがあります。 これは、自然階層と呼ばれることがあります。 エンド ユーザーは、階層を使用してキューブ データを参照できます。 階層を定義するには、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のディメンション デザイナーの [階層] ペインを使用します。  
  
 ユーザー定義階層を作成すると、階層は *不規則*になる場合があります。 不規則階層とは、少なくとも 1 つのメンバーの論理上の親メンバーが、そのメンバーのすぐ上のレベルにない階層です。 不規則階層を使用している場合は、欠落しているメンバーを表示するかどうか、および欠落しているメンバーを表示する方法を制御する設定があります。 詳細については、「 [不規則階層](user-defined-hierarchies-ragged-hierarchies.md)」を参照してください。  
  
> [!NOTE]  
>  ユーザー定義階層のデザインと構成に関連するパフォーマンスの問題の詳細については、「 [SQL Server 2005 Analysis Services パフォーマンス ガイド](http://go.microsoft.com/fwlink/?LinkId=81621)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [ユーザー階層プロパティ](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md)   
 [レベル プロパティ&#91;機能強化&#93;](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-level-properties.md)   
 [親子階層](parent-child-dimension.md)  
  
  
