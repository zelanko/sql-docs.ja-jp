---
title: 標準のリレーションシップとファクト リレーションシップのプロパティの定義 |Microsoft Docs
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
- granularity attribute
- relationships [Analysis Services], regular relationships
ms.assetid: 840280d8-20c3-46c0-99ea-62479469c36b
caps.latest.revision: 9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: dbf4b0f179c0c4ba0990b8fe61b2cd2a7584f058
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37211932"
---
# <a name="define-a-regular-relationship-and-regular-relationship-properties"></a>ファクト リレーションシップとファクト リレーションシップのプロパティの定義
  新しいキューブ ディメンションまたは新しいメジャー グループが定義されると、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、標準リレーションシップが存在するかどうかを検出し、ディメンションの使用法を `Regular` に設定しようと試みます。 標準ディメンションのリレーションシップはキューブ デザイナーの **[ディメンションの使用法]** タブで表示または編集できます。  
  
 キューブ ディメンションとメジャー グループ間のリレーションシップを定義する場合は、粒度属性もそのリレーションシップに指定します。 粒度属性では、そのディメンションのキューブで使用できる最も低い詳細レベルを定義します (通常はディメンションのキー属性)。 ただし、特定のメジャー グループ内の特定のキューブ ディメンションの粒度を別のレベルに設定することが必要な場合もあります。 たとえば、Sales Quotas メジャー グループまたは Budget メジャー グループを使用する場合、Time ディメンションの粒度属性を Day 属性ではなく Month 属性に設定できます。 粒度属性をキー属性以外の属性に指定する場合は、ディメンション内の他のすべての属性が、属性リレーションシップを介してこの属性に直接または間接的にリンクされるようにする必要があります。 リンクされていない属性があると、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] でデータを適切に集計できなくなります。  
  
  
