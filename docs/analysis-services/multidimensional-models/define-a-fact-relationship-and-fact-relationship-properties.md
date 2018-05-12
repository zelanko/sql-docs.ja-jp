---
title: ファクト リレーションシップとファクト リレーションシップのプロパティの定義 |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2341335d1d9c4904e1832e0a8087c0fa8198fd58
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="define-a-fact-relationship-and-fact-relationship-properties"></a>ファクト リレーションシップとファクト リレーションシップのプロパティの定義
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  新しいキューブ ディメンションまたは新しいメジャー グループが定義されると、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、ファクト ディメンションのリレーションシップが存在するかどうかを検出し、ディメンションの使用法を **[ファクト]** に設定しようと試みます。 ファクト ディメンションのリレーションシップはキューブ デザイナーの **[ディメンションの使用法]** タブで表示または編集できます。 ディメンションとメジャー グループ間のファクト リレーションシップには次の制約があります。  
  
-   1 つのキューブ ディメンションには、特定のメジャー グループに対してファクト リレーションシップを 1 つだけ設定できます。  
  
-   1 つのキューブ ディメンションには、複数のメジャー グループに対して個別のファクト リレーションシップを設定できます。  
  
-   リレーションシップの粒度属性は、ディメンションのキー属性 (取引番号など) である必要があります。 これにより、ディメンションとファクト テーブル内のファクトとの間に一対一リレーションシップが作成されます。  
  
  
