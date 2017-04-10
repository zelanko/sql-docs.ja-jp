---
title: "標準リレーションシップおよび標準リレーションシップ プロパティの定義 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "粒度属性 (granularity attribute)"
  - "リレーションシップ [Analysis Services], 標準リレーションシップ"
ms.assetid: 840280d8-20c3-46c0-99ea-62479469c36b
caps.latest.revision: 9
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 9
---
# 標準リレーションシップおよび標準リレーションシップ プロパティの定義
  新しいキューブ ディメンションまたは新しいメジャー グループが定義されると、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、標準リレーションシップが存在するかどうかを検出し、ディメンションの使用法を **正規** に設定しようと試みます。 標準ディメンションのリレーションシップはキューブ デザイナーの **[ディメンションの使用法]** タブで表示または編集できます。  
  
 キューブ ディメンションとメジャー グループ間のリレーションシップを定義する場合は、粒度属性もそのリレーションシップに指定します。 粒度属性では、そのディメンションのキューブで使用できる最も低い詳細レベルを定義します (通常はディメンションのキー属性)。 ただし、特定のメジャー グループ内の特定のキューブ ディメンションの粒度を別のレベルに設定することが必要な場合もあります。 たとえば、Sales Quotas メジャー グループまたは Budget メジャー グループを使用する場合、Time ディメンションの粒度属性を Day 属性ではなく Month 属性に設定できます。 粒度属性をキー属性以外の属性に指定する場合は、ディメンション内の他のすべての属性が、属性リレーションシップを介してこの属性に直接または間接的にリンクされるようにする必要があります。 リンクされていない属性があると、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] でデータを適切に集計できなくなります。  
  
  