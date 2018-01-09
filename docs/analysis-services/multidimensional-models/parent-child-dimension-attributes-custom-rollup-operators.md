---
title: "親子ディメンションのカスタム ロールアップ演算子 |Microsoft ドキュメント"
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
- child rollup operations
- UnaryOperatorColumn property
- custom rollup operators [Analysis Services]
- unary operators
- parent-child dimensions [Analysis Services]
ms.assetid: a3ddd9fc-5fa3-4227-9322-8c45a5b5c2c3
caps.latest.revision: "26"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 84ed7fd34e017fe0ea076822d1931ea1143b5849
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="parent-child-dimension-attributes---custom-rollup-operators"></a>親子ディメンションの属性のカスタム ロールアップ演算子
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]カスタム ロールアップ演算子では、メンバーの値を親子階層で親の値にどのようにロールアップする方法を制御する簡単な方法を提供します。 親子リレーションシップを含んでいるディメンションでは、親属性のすべての計算されないメンバーのロールアップを指定する単項演算子を含んでいる列を指定します。 単項演算子は、親メンバーの値が評価されるたびにメンバーに適用されます。  
  
 単項演算子は、親属性の **UnaryOperatorColumn** プロパティで定義した列に保存され、属性の各メンバーに適用されます。 このプロパティで指定する列は、ディメンション テーブルに存在するか、ディメンション テーブル内の外部キーによってそのディメンション テーブルに関連付けられているテーブルに存在する可能性があります。  
  
 カスタム ロールアップ演算子の機能は、カスタム メンバー式に似ていますが、それよりも簡単です。 カスタム メンバー式では、多次元式 (MDX) を使用して、メンバーのロール アップ方法を決定します。 これに対し、カスタム ロールアップ演算子では、単純な単項演算子を使用して、メンバーの値が親に与える影響を決定します。 ディメンション内の前のレベルのカスタム メンバー式は、レベルのカスタム ロールアップ演算子を上書きします。  
  
## <a name="custom-rollup-precedence"></a>カスタム ロールアップの優先順位  
 優先順位の面では、階層内のレベルのソース属性のカスタム ロールアップ演算子は、前のレベルのカスタム メンバー式に優先します。 ただし、前のレベルのカスタムメンバー式は、レベルのカスタム ロールアップ演算子を上書きします。  
  
## <a name="see-also"></a>参照  
 [カスタム メンバー式の定義](../../analysis-services/multidimensional-models/attribute-properties-define-custom-member-formulas.md)   
 [親子ディメンションの単項演算子](../../analysis-services/multidimensional-models/parent-child-dimension-attributes-unary-operators.md)  
  
  
