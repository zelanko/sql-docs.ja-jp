---
title: "標準リレーションシップおよび標準リレーションシップ プロパティの定義 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
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
- granularity attribute
- relationships [Analysis Services], regular relationships
ms.assetid: 840280d8-20c3-46c0-99ea-62479469c36b
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: bc2ee7a49cddc8b5d6b0ce0905e2cbcd084a8897
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="define-a-regular-relationship-and-regular-relationship-properties"></a>標準リレーションシップおよび標準リレーションシップ プロパティの定義
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
新しいキューブ ディメンションまたは新しいメジャー グループが定義されると、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、標準リレーションシップが存在するかどうかを検出し、ディメンションの使用法を **正規**に設定しようと試みます。 標準ディメンションのリレーションシップはキューブ デザイナーの **[ディメンションの使用法]** タブで表示または編集できます。  
  
 キューブ ディメンションとメジャー グループ間のリレーションシップを定義する場合は、粒度属性もそのリレーションシップに指定します。 粒度属性では、そのディメンションのキューブで使用できる最も低い詳細レベルを定義します (通常はディメンションのキー属性)。 ただし、特定のメジャー グループ内の特定のキューブ ディメンションの粒度を別のレベルに設定することが必要な場合もあります。 たとえば、Sales Quotas メジャー グループまたは Budget メジャー グループを使用する場合、Time ディメンションの粒度属性を Day 属性ではなく Month 属性に設定できます。 粒度属性をキー属性以外の属性に指定する場合は、ディメンション内の他のすべての属性が、属性リレーションシップを介してこの属性に直接または間接的にリンクされるようにする必要があります。 リンクされていない属性があると、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] でデータを適切に集計できなくなります。  
  
  
