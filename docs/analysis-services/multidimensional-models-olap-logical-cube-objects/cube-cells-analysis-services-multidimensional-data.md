---
title: キューブ セル (Analysis Services - 多次元データ) |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 71525eb212bebfbb06f747311d1791ddfd43cfdd
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63042413"
---
# <a name="cube-cells-analysis-services---multidimensional-data"></a>キューブ セル (Analysis Services - 多次元データ)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  キューブはメジャー グループとディメンションで編成されたセルで構成されています。 セルは、キューブ内の各ディメンションの 1 メンバーのキューブ内の論理的な一意の交差部分を表します。 たとえば、次のダイアグラムで示すキューブには、Source、Route、Time という 3 つのディメンションで編成された 2 つのメジャーを持つメジャー グループが 1 つ含まれています。  
  
 ![1 つのセルを示すキューブ図](../../analysis-services/multidimensional-models-olap-logical-cube-objects/media/as-cubeintro5.gif "1 つのセルを示すキューブ図")  
  
 このダイアグラムの 1 つの影付きセルは、次のメンバーの交差部分です。  
  
-   Route ディメンションの air メンバー  
  
-   Source ディメンションの Africa メンバー  
  
-   Time ディメンションの 4th quarter メンバー  
  
-   Packages メジャー  
  
## <a name="leaf-and-nonleaf-cells"></a>リーフ セルと非リーフ セル  
 キューブ内のセルの値は複数の方法で取得できます。 前の例では、セルの値直接から取得できます、キューブのファクト テーブルのセルの識別に使用されるすべてのメンバーが*リーフ メンバー*します。 階層的にはリーフ メンバーに子メンバーはなく、通常はディメンション テーブルの 1 つのレコードを参照しています。 このようなセルと呼びます、*リーフ セル*します。  
  
 ただし、セルを確認できますを使用して*非リーフ メンバー*します。 非リーフ メンバーとは、1 つ以上の子メンバーを持っているメンバーです。 この場合、セルの値は通常、非リーフ メンバーに関連付けられている子メンバーの集計から取得されます。 たとえば、次のメンバーとディメンションの交差部分では、集計によって値が指定されるセルを参照します。  
  
-   Route ディメンションの air メンバー  
  
-   Source ディメンションの Africa メンバー  
  
-   Time ディメンションの 2nd half メンバー  
  
-   Packages メンバー  
  
 Time ディメンションの 2nd half メンバーは非リーフ メンバーです。 そのため、次のダイアグラムに示すように、2nd half メンバーに関連付けられているすべての値を集計する必要があります。  
  
 ![2 nd half メンバーの 3 番目および 4 番目の四半期セル](../../analysis-services/multidimensional-models-olap-logical-cube-objects/media/as-cubeintro6.gif "2 nd half メンバーの 3 番目および 4 番目の四半期セル")  
  
 3rd quarter と 4th quarter の各メンバーの集計が合計であると仮定すると、指定したセルの値は、前のダイアグラムの影付きリーフ セルすべてを合計した 400 です。 指定したセルのセルの値は、他のセルの集計から派生するのでと見なされます、*非リーフ セル*します。  
  
 カスタム メンバーだけでなくカスタム ロールアップやメンバー グループも使用しているメンバーのセルの値も、同様に取得されます。 ただし、計算されるメンバーのセルの値は、計算されるメンバーの定義に使用した多次元式 (MDX) 式に完全に基づいて取得されるため、場合によっては、実際のセル データは関係しないこともあります。 詳細については、次を参照してください。 [、親子ディメンションのカスタム ロールアップ演算子](../../analysis-services/multidimensional-models/parent-child-dimension-attributes-custom-rollup-operators.md)、[カスタム メンバー式の定義](../../analysis-services/multidimensional-models/attribute-properties-define-custom-member-formulas.md)、および[計算](../../analysis-services/multidimensional-models-olap-logical-cube-objects/calculations.md)します。  
  
## <a name="empty-cells"></a>空のセル  
 キューブ内のすべてのセルに値が必要なわけではありません。キューブには、データのない交差部分もあります。 このような交差部分は空のセルと呼ばれ、キューブ内にしばしば発生します。これは、キューブ内にメジャーを持つディメンション属性のすべての交差部分に、ファクト テーブル内の対応するレコードが含まれているとは限らないからです。 キューブ内のセルの合計数に対するキューブ内の空のセルの比率として呼ば、*希薄*キューブの。  
  
 たとえば、次のダイアグラムに示すキューブは、このトピックの他の例に似ていますが、 この例では、第 3 四半期の Africa または第 4 四半期の Australia への air による出荷が含まれていません。 これらのディメンションとメジャーの交差部分に対応するデータはファクト テーブルにありません。そのため、この交差部分にあるセルは空になります。  
  
 ![空のセルを示すキューブ図](../../analysis-services/multidimensional-models-olap-logical-cube-objects/media/as-cubeintro7.gif "空のセルを示すキューブ図")  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、空のセルは特殊な品質を保持するセル。 空のセルは、相互結合、カウントなどの結果を非対称にできるため、多くの MDX 関数は、計算のために空のセルを無視する機能を提供しています。 詳細については、次を参照してください。[多次元式&#40;MDX&#41;参照](../../mdx/multidimensional-expressions-mdx-reference.md)、および[MDX の主な概念&#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md)します。  
  
## <a name="security"></a>セキュリティ  
 セル データへのアクセスは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のロール レベルで管理され、MDX 式を使用して細かく制御できます。 詳細については、次を参照してください。[ディメンション データへのカスタム アクセス権を付与&#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-custom-access-to-dimension-data-analysis-services.md)、および[セル データへのカスタム アクセス権を付与&#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-custom-access-to-cell-data-analysis-services.md)します。  
  
## <a name="see-also"></a>参照  
 [キューブのストレージ&#40;Analysis Services - 多次元データ&#41;](../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-storage-analysis-services-multidimensional-data.md)   
 [集計と集計デザイン](../../analysis-services/multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)  
  
  
