---
title: 参照リレーションシップを定義し、リレーションシップのプロパティを参照 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- referenced dimension relationship
- relationships [Analysis Services], referenced dimensions
ms.assetid: 5bb44b41-635b-4398-8fe9-0bfbb142553e
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 845ec8020ece6d253d4c025b960081a801123a0c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36177864"
---
# <a name="define-a-referenced-relationship-and-referenced-relationship-properties"></a>参照リレーションシップと参照リレーションシップのプロパティの定義
  参照ディメンションのリレーションシップは、キューブ デザイナーの **[ディメンションの使用法]** タブで定義します。 参照ディメンションのリレーションシップを定義するには、以下を指定します。  
  
-   結合先の中間ディメンション。 標準ディメンションまたは別の参照ディメンションを指定します。  
  
-   ディメンションがメジャー グループについての集計に使用できる最も低いレベルを定義する参照ディメンション属性。  
  
-   参照ディメンション属性に対応する中間ディメンションの (外部キー) 属性。  
  
 通常、参照ディメンションをファクト テーブルにリンクする列は参照ディメンションのキー属性ですが、この列を中間ディメンションの属性として定義する必要もあります。 参照ディメンションのチェーンを作成する場合は、まず、チェーンの最初のディメンションとメジャー グループ間に標準のリレーションシップを作成します。 次に、追加の各参照リレーションシップを順に作成します。 参照リレーションシップは、メジャー グループとのリレーションシップが既にあるディメンションに対してのみ作成できます。  
  
 参照ディメンションのリレーションシップを作成すると、ディメンション属性のリンクが既定で具体化されます。 ディメンション属性のリンクを具体化すると、各行のファクト テーブルおよび参照ディメンション間のリンクの値が具体化され、処理中にディメンションの MOLAP 構造に格納されます。 この操作を行うと、処理パフォーマンスやストレージの要件にわずかに影響しますが、クエリ パフォーマンスの向上を図ることができます。  
  
 参照ディメンションでは、参照ディメンションと参照ディメンションのメイン テーブルに対応するメジャー グループ間のリレーションシップを定義する属性を特定することにより、粒度が指定されます。 複数の参照ディメンションを連結すると、最も外側のディメンションからメジャー グループまでのリレーションシップが参照によって定義されます。  
  
  