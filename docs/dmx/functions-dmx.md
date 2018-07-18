---
title: 関数 (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3f0fce34f57591d9c6c3f3a9c7382266d655f364
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37985449"
---
# <a name="functions-dmx"></a>関数 (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  クエリのオブジェクトへのデータ マイニング拡張機能 (DMX) の使用と[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、データ マイニング モデルまたは入力データセット内の列に値だけをより多くの情報を返す関数を使用することができます。 たとえば、DMX クエリを使用して、予測が正しい可能性が高いとしても、列の予測値だけを返さないようにすることができます。 DMX 関数だけでなく、Microsoft Visual Basic for Applications (VBA)、Microsoft Excel、およびストアド プロシージャの関数を使用することもできます。  
  
## <a name="dmx-functions"></a>DMX 関数  
 DMX 関数は、次のタスクの実行に使用できます。  
  
-   予測を返す。  
  
-   確立およびサポートなど、予測についての統計情報を返す。  
  
-   クエリ結果をフィルターする。  
  
-   テーブル式を並べ替える。  
  
 ほとんどの DMX 関数は、予測のサポートなど、スカラー値を返します。しかし、いくつかは表形式の結果を返します。 たとえば、PredictHistogram 関数は、サポートと、指定した予測可能列の各状態用の確率を含むテーブルを返します。 結果は、新しい表形式の列として表示されます。  
  
 **詳細情報:** [一般的な予測関数&#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)、[データ マイニング拡張機能&#40;DMX&#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)  
  
## <a name="visual-basic-for-applications-vba-and-excel-functions"></a>Visual Basic for Applications (VBA) と Excel 関数  
 さらに、DMX 関数は、DMX ステートメントからさまざまな VBA と Excel の関数を呼び出すこともできます。 たとえば、lCase 関数を使用すると、TM_Decision_Tree モデル コンテンツ内の Attribute_Name 列の表示方法を変更します。 次のサンプル コードにこれを示します。  
  
```  
SELECT lCase([Attribute_Name])   
FROM [TM_Decision_Tree].CONTENT  
```  
  
 VBA と Excel の両方で同じ関数が存在する場合は、いずれかを使用して、DMX ステートメントで関数名を付ける必要があります**VBA**または**Excel**します。 たとえば、使用すると`VBA!Log`または`Excel!Log`します。 使用する VBA または Excel の関数が DMX または多次元式 (MDX) にも存在する場合、あるいは関数にドル記号 ($) が含まれる場合、角かっこを使用して関数をエスケープする必要があります。 たとえば、関数呼び出しは `[VBA!Format]` のようになります。  
  
## <a name="stored-procedures"></a>ストアド プロシージャ  
 共通言語ランタイム プログラミング言語を使用して、DMX の機能を拡張するストアド プロシージャを作成できます。 たとえば、回帰ツリー マイニング モデルは、A、B などの係数を返しますと、回帰式を記述するためですが、モデルには、A+bx などの式自体は返しません。 = y です。 ただし、データ マイニング モデル オブジェクトを使用して、コンテンツ スキーマを操作し、出力として回帰式を返すストアド プロシージャは記述できます。 この場合、DMX ステートメントは、クエリ結果の一部として回帰式の一覧を返すことができます。  
  
 **詳細情報:** [多次元モデルのアセンブリの管理](../analysis-services/multidimensional-models/multidimensional-model-assemblies-management.md)  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能&#40;DMX&#41;リファレンス](../dmx/data-mining-extensions-dmx-reference.md)   
 [データ マイニング拡張機能&#40;DMX&#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [データ マイニング拡張機能&#40;DMX&#41;演算子リファレンス](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [データ マイニング拡張機能&#40;DMX&#41;ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)   
 [データ マイニング拡張機能&#40;DMX&#41;構文表記規則](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [データ マイニング拡張機能&#40;DMX&#41;構文要素](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [一般的な予測関数&#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [構造と DMX 予測クエリの使用](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [DMX 選択ステートメントについて](../dmx/understanding-the-dmx-select-statement.md)  
  
  
