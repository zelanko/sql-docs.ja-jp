---
title: 計算コンテキスト |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: mdx
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 193855717a055fbe0ae4d1b49ae98e30e44b86a5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="calculation-context"></a>計算コンテキスト
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  計算コンテキストとは、式が評価され、すべての座標が明示的に知られているか、または式から派生することができる、キューブの既知のサブ空間です。  
  
## <a name="determining-the-calculation-context"></a>計算コンテキストの決定  
 すべてのセット、メンバー、組、数値関数は、MDX 式またはステートメント全体のコンテキストで実行されます。 組などの引数を関数に渡す際には、キューブ空間内の一部の座標のみが明示的に指定されます。 その他の座標は現在の計算コンテキストを基に取得されます。  
  
 指定のないセル座標と属性メンバーの計算コンテキストは、次の順序で決定されます。  
  
1.  FROM 句 (該当する場合) : キューブ全体、または SELECT ステートメントの形式でサブキューブを指定できます。  
  
2.  WHERE 句 (該当する場合) : *スライサー軸*ともいいます。この軸に、クエリの列と行の軸で返されるメンバーを制限するセット、組、メンバーを指定します。 概念上、列または行の軸で明示的に指定されていないすべての属性階層の既定のメンバーは、スライサー軸の一部として使用されます。  
  
    > [!NOTE]  
    >  特定の属性のセル座標がスライサー軸とそれ以外の軸で指定されている場合、軸のセットのメンバーを決定する際に、関数で指定されている座標が優先的に使用されることがあります。 [Filter (MDX)](../../../mdx/filter-mdx.md) 関数および [Order (MDX)](../../../mdx/order-mdx.md) 関数はその例です。WHERE 句、または FROM 句の SELECT ステートメントによって計算コンテキストから除外された属性メンバーを使用して、結果の絞り込みや順序指定ができます。  
  
3.  クエリまたは式で定義されている、名前付きセットと計算されるメンバー。  
  
4.  行軸および列軸で指定された組とセット : 行軸、列軸、またはスライサー軸に出現しない属性については、既定のメンバーが使用されます。  
  
5.  各軸上のキューブ セルまたはサブキューブ セル : 軸上の空の組が削除され、HAVING 句が適用されます。  
  
6.  詳細については、次を参照してください[クエリ & #40; 内のキューブ コンテキストの確立。MDX と #41 です。](../../../analysis-services/multidimensional-models/mdx/establishing-cube-context-in-a-query-mdx.md)  
  
 次のクエリでは、WHERE 句で指定されている Country 属性のメンバーと Calendar Year 属性のメンバーによって、行軸の計算コンテキストを制限しています。  
  
```  
SELECT Customer.City.City.Members ON 0  
FROM [Adventure Works]  
WHERE (Customer.Country.France, [Date].[Calendar].[Calendar Year].[CY 2004],  
   Measures.[Internet Sales Amount])  
```  
  
 このクエリを修正して、行軸に **FILTER** 関数を指定し、この **FILTER** 関数に Calendar Year 属性階層のメンバーを指定した場合、列軸上のセットのメンバーに対して計算コンテキストを指定している Calendar Year 属性階層の属性メンバーを変更できます。  
  
```  
SELECT FILTER  
   (  
      Customer.City.City.Members,   
         ([Date].[Calendar].[Calendar Year].[CY 2003],  
            Measures.[Internet Order Quantity]) > 75   
   ) ON 0  
FROM [Adventure Works]  
WHERE (Customer.Country.France,  
   [Date].[Calendar].[Calendar Year].[CY 2004],  
   Measures.[Internet Sales Amount])  
```  
  
 上のクエリで、Calendar Year 属性階層の通常の計算コンテキストは CY 2004 ですが、列軸に表示する組のセルの計算コンテキストは、Calendar Year 属性階層の CY 2003 メンバーによってフィルター処理されています。 さらに、Internet Order Quantity メジャーによるフィルター処理も行われています。 ただし、列軸のセット メンバーがいったん設定されると、列軸に表示されるメンバーの値に対する計算コンテキストは、WHERE 句によって決定されます。  
  
> [!IMPORTANT]  
>  クエリのパフォーマンスを向上するには、解決プロセスのできるだけ早い段階でメンバーおよび組を削除してください。 こうすることで、最終的なメンバーのセットに対するクエリ時の複雑な計算を、最小限のセルに対して行うことができます。  
  
## <a name="see-also"></a>参照  
 [クエリ & #40; 内のキューブ コンテキストの確立MDX と #41 です。](../../../analysis-services/multidimensional-models/mdx/establishing-cube-context-in-a-query-mdx.md)   
 [MDX クエリの基礎と #40 です。Analysis Services & #41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)   
 [MDX & #40; の主な概念Analysis Services & #41;](../../../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md)  
  
  
