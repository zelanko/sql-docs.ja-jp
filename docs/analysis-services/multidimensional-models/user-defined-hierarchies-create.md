---
title: ユーザー定義階層を作成 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- user-defined hierarchies [Analysis Services]
ms.assetid: 16715b85-0630-4a8e-99b0-c0d213cade26
caps.latest.revision: 22
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 64369f5abba3e8aa09c30a7ffdfbee6d5786b9ec
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="user-defined-hierarchies---create"></a>ユーザー定義階層を作成します。
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]ユーザー定義階層を作成することができます。 階層とは、属性に基づいたレベルのコレクションのことです。 たとえば、時間階層には、年、四半期、月、週、および日の各レベルが含まれる場合があります。 階層によっては、各メンバー属性が、その上位にあるメンバー属性を一意に示すことがあります。 これは、自然階層と呼ばれることがあります。 エンド ユーザーは、階層を使用してキューブ データを参照できます。 階層を定義するには、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のディメンション デザイナーの [階層] ペインを使用します。  
  
 ユーザー定義階層を作成すると、階層は *不規則*になる場合があります。 不規則階層とは、少なくとも 1 つのメンバーの論理上の親メンバーが、そのメンバーのすぐ上のレベルにない階層です。 不規則階層を使用している場合は、欠落しているメンバーを表示するかどうか、および欠落しているメンバーを表示する方法を制御する設定があります。 詳細については、「 [不規則階層](../../analysis-services/multidimensional-models/user-defined-hierarchies-ragged-hierarchies.md)」を参照してください。  
  
> [!NOTE]  
>  ユーザー定義階層のデザインと構成に関連するパフォーマンスの問題の詳細については、「 [SQL Server 2005 Analysis Services パフォーマンス ガイド](http://go.microsoft.com/fwlink/?LinkId=81621)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [ユーザー階層プロパティ](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md)   
 [レベルのプロパティ - ユーザー階層](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies-level-properties.md)   
 [親子ディメンション](../../analysis-services/multidimensional-models/parent-child-dimension.md)  
  
  
