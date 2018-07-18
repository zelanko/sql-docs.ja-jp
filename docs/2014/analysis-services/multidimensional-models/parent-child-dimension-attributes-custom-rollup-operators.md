---
title: 親子ディメンションのカスタム ロールアップ演算子 |Microsoft Docs
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
- child rollup operations
- UnaryOperatorColumn property
- custom rollup operators [Analysis Services]
- unary operators
- parent-child dimensions [Analysis Services]
ms.assetid: a3ddd9fc-5fa3-4227-9322-8c45a5b5c2c3
caps.latest.revision: 26
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e6dcee2c6cb88e071d55c5cb1a7d6c131c31a5f9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37272008"
---
# <a name="custom-rollup-operators-in-parent-child-dimensions"></a>親子ディメンションのカスタム ロールアップ演算子
  カスタム ロールアップ演算子を使用すると、親子階層でメンバーの値を親の値にロール アップする方法を簡単に制御できます。 親子リレーションシップを含んでいるディメンションでは、親属性のすべての計算されないメンバーのロールアップを指定する単項演算子を含んでいる列を指定します。 単項演算子は、親メンバーの値が評価されるたびにメンバーに適用されます。  
  
 単項演算子は、親属性の `UnaryOperatorColumn` プロパティで定義した列に保存され、属性の各メンバーに適用されます。 このプロパティで指定する列は、ディメンション テーブルに存在するか、ディメンション テーブル内の外部キーによってそのディメンション テーブルに関連付けられているテーブルに存在する可能性があります。  
  
 カスタム ロールアップ演算子の機能は、カスタム メンバー式に似ていますが、それよりも簡単です。 カスタム メンバー式では、多次元式 (MDX) を使用して、メンバーのロール アップ方法を決定します。 これに対し、カスタム ロールアップ演算子では、単純な単項演算子を使用して、メンバーの値が親に与える影響を決定します。 ディメンション内の前のレベルのカスタム メンバー式は、レベルのカスタム ロールアップ演算子をオーバーライドします。  
  
## <a name="custom-rollup-precedence"></a>カスタム ロールアップの優先順位  
 優先順位の面では、階層内のレベルのソース属性のカスタム ロールアップ演算子は、前のレベルのカスタム メンバー式をオーバーライドします。 ただし、前のレベルのカスタムメンバー式は、レベルのカスタム ロールアップ演算子をオーバーライドします。  
  
## <a name="see-also"></a>参照  
 [カスタム メンバー式を定義します。](attribute-properties-define-custom-member-formulas.md)   
 [親子ディメンションの単項演算子](parent-child-dimension-attributes-unary-operators.md)  
  
  
