---
title: 演算子 (DMX) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- DMX
helpviewer_keywords:
- operators [DMX]
- DMX [Analysis Services], operators
- Data Mining Extensions [Analysis Services], operators
ms.assetid: e453e570-1ad1-4604-892f-6130308936ac
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: d55ce9059ddee559ae6c9d214f5a8b05457abb86
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="operators-dmx"></a>演算子 (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  内のクエリで算術演算子、比較、連結、および論理演算を実行するデータ マイニング拡張機能 (DMX) 演算子を使用することができます[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]です。  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 演算子を使用して、次の操作を実行します。  
  
-   特定の条件を満たしている値またはオブジェクトの検索  
  
-   値の間または式の間での判断  
  
 DMX では、複数のカテゴリの演算子を使用します。これについては、次のセクションで説明します。 個々 の演算子の詳細については、次を参照してください。[データ マイニング拡張機能&#40;DMX&#41;演算子リファレンス](../dmx/data-mining-extensions-dmx-operator-reference.md)です。  
  
|演算子のカテゴリ|演算子の型|  
|-----------------------|-----------------------|  
|[算術演算子&#40;DMX&#41;](../dmx/operators-arithmetic.md)|加算、減算、乗算、除算を実行します。|  
|[比較演算子&#40;DMX&#41;](../dmx/operators-comparison.md)|1 つの値を別の値または式を比較します。|  
|[論理演算子&#40;DMX&#41;](../dmx/operators-logical.md)|条件の真偽を調べます (AND、OR、NOT など)。|  
|[単項演算子&#40;DMX&#41;](../dmx/operators-unary.md)|1 つのオペランドに対して演算を実行します。|  
  
 演算子を使用することで、DMX の短い式を組み合わせて、より複雑な式を作成することができます。 基づく順序で複雑な式は、演算子が評価されます、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]演算子の優先順位の定義。 優先順位の高い演算子は、優先順位の低い演算子より先に実行されます。 式の詳細については、次を参照してください。[式&#40;DMX&#41;](../dmx/expressions-dmx.md)です。  
  
 複数の単純式を 1 つの複合式に結合する場合、結合した式のデータ型は、演算子のルールとデータ型の優先順位のルールが組み合わされて決定されます。 結果が文字または Unicode 値では場合、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]演算子の照合順序の優先順位の規則と規則を組み合わせることによって、結果の照合順序を決定します。 単純式の有効桁数、小数点以下桁数、長さに基づいて結果の有効桁数、小数点以下桁数、長さを指定するルールもあります。  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能 (&) #40";"DMX"&"#41;参照](../dmx/data-mining-extensions-dmx-reference.md)   
 [データ マイニング拡張機能 (&) #40";"DMX"&"#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [データ マイニング拡張機能 (&) #40";"DMX"&"#41;ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)   
 [データ マイニング拡張機能&#40;DMX&#41;構文表記規則](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [データ マイニング拡張機能&#40;DMX&#41;構文要素](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [一般的な予測関数 (&) #40";"DMX"&"#41;](../dmx/general-prediction-functions-dmx.md)   
 [構造と DMX 予測クエリの使用状況](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [DMX 選択ステートメントについて](../dmx/understanding-the-dmx-select-statement.md)  
  
  
