---
title: "式 (DMX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- DMX
helpviewer_keywords:
- Data Mining Extensions [Analysis Services], expressions
- DMX [Analysis Services], expressions
- expressions [DMX]
ms.assetid: 00579552-19c8-4e9d-a790-f88df3e1aeea
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: c04c55fc461d4429d55d32a776f5bea8eca345e8
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="expressions-dmx"></a>式 (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データ マイニング拡張機能 (DMX)、式は、識別子、値、および演算子の組み合わせを[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]結果を取得するを評価できます。  
  
 DMX 式には、簡単なものも複雑なものもあります。 簡単な式としては、次のようなものがあります。  
  
 定数  
 定数は 1 つの特定の値を表す記号です。 定数には、文字列、または数値や日付値を使用できます。 文字定数および日付定数を区切るには、単一引用符 (') を使用する必要があります。  
  
 スカラー関数  
 スカラー関数は 1 つの値を返します。  
  
 Non-Scalar Function  
 非スカラー関数はテーブルを返します。  
  
 Object Identifier  
 オブジェクト識別子は、DMX の簡単な式と見なすことができます。  
  
 複雑な式を作成するには、演算子を使用して、これらの式を組み合わせます。 演算子の詳細については、次を参照してください[データ マイニング拡張機能 (&) #40";"DMX"&"#41;。演算子リファレンス](../dmx/data-mining-extensions-dmx-operator-reference.md)です。  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能 (&) #40";"DMX"&"#41;参照](../dmx/data-mining-extensions-dmx-reference.md)   
 [データ マイニング拡張機能 (&) #40";"DMX"&"#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [データ マイニング拡張機能 (&) #40";"DMX"&"#41;ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)   
 [データ マイニング拡張機能 (&) #40";"DMX"&"#41;構文表記規則](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [データ マイニング拡張機能 (&) #40";"DMX"&"#41;構文要素](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [一般的な予測関数 (&) #40";"DMX"&"#41;](../dmx/general-prediction-functions-dmx.md)   
 [構造と DMX 予測クエリの使用状況](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [DMX の Select ステートメントを理解します](../dmx/understanding-the-dmx-select-statement.md)  
  
  

