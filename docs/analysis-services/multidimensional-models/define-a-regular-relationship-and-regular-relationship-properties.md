---
title: "標準リレーションシップおよび標準リレーションシップ プロパティの定義 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- granularity attribute
- relationships [Analysis Services], regular relationships
ms.assetid: 840280d8-20c3-46c0-99ea-62479469c36b
caps.latest.revision: "9"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 10025f3c362a0be45d782644ca36a41661e13c68
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="define-a-regular-relationship-and-regular-relationship-properties"></a>標準リレーションシップおよび標準リレーションシップ プロパティの定義
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]新しいキューブ ディメンションまたは新しいメジャー グループを定義するときに[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]は標準のリレーションシップが存在しにディメンションの使用法の設定を設定し、かどうかを検出しよう**正規**です。 標準ディメンションのリレーションシップはキューブ デザイナーの **[ディメンションの使用法]** タブで表示または編集できます。  
  
 キューブ ディメンションとメジャー グループ間のリレーションシップを定義する場合は、粒度属性もそのリレーションシップに指定します。 粒度属性では、そのディメンションのキューブで使用できる最も低い詳細レベルを定義します (通常はディメンションのキー属性)。 ただし、特定のメジャー グループ内の特定のキューブ ディメンションの粒度を別のレベルに設定することが必要な場合もあります。 たとえば、Sales Quotas メジャー グループまたは Budget メジャー グループを使用する場合、Time ディメンションの粒度属性を Day 属性ではなく Month 属性に設定できます。 粒度属性をキー属性以外の属性に指定する場合は、ディメンション内の他のすべての属性が、属性リレーションシップを介してこの属性に直接または間接的にリンクされるようにする必要があります。 リンクされていない属性があると、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] でデータを適切に集計できなくなります。  
  
  
