---
title: "ファクト リレーションシップとファクト リレーションシップのプロパティの定義 |Microsoft ドキュメント"
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
helpviewer_keywords: fact dimensions [Analysis Services]
ms.assetid: d8e41724-da77-4ac1-bc42-956b5d91ea5d
caps.latest.revision: "10"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e1e58f9616fc40ad895858a6eb6b3cfa7e0bbed1
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="define-a-fact-relationship-and-fact-relationship-properties"></a>ファクト リレーションシップとファクト リレーションシップのプロパティの定義
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]新しいキューブ ディメンションまたは新しいメジャー グループを定義するときに[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]はファクト ディメンション リレーションシップが存在し、ディメンションの使用法の設定を設定します検出しよう**ファクト**です。 ファクト ディメンションのリレーションシップはキューブ デザイナーの **[ディメンションの使用法]** タブで表示または編集できます。 ディメンションとメジャー グループ間のファクト リレーションシップには次の制約があります。  
  
-   1 つのキューブ ディメンションには、特定のメジャー グループに対してファクト リレーションシップを 1 つだけ設定できます。  
  
-   1 つのキューブ ディメンションには、複数のメジャー グループに対して個別のファクト リレーションシップを設定できます。  
  
-   リレーションシップの粒度属性は、ディメンションのキー属性 (取引番号など) である必要があります。 これにより、ディメンションとファクト テーブル内のファクトとの間に一対一リレーションシップが作成されます。  
  
  
