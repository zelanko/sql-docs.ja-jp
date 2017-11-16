---
title: "キューブ セル (Analysis Services - 多次元データ) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- storing data [Analysis Services], cells
- hierarchies [Analysis Services], cells
- OLAP objects [Analysis Services], cells
- data members [Analysis Services]
- cubes [Analysis Services], cells
- empty cells [Analysis Services]
- nonleaf members
- cubes [Analysis Services], examples
- storage [Analysis Services], cells
- nonleaf cells
- calculated cells [Analysis Services]
- dimensions [Analysis Services], cells
- cells [Analysis Services]
- leaf members
- leaf cells
ms.assetid: 9945773c-a43b-40d4-91cf-3d2ebc90bca5
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7da5c513675b85a209e76da5787828eb31be24f8
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="cube-cells-analysis-services---multidimensional-data"></a>キューブ セル (Analysis Services - 多次元データ)
  キューブはメジャー グループとディメンションで編成されたセルで構成されています。 セルは、キューブ内の各ディメンションの 1 メンバーのキューブ内の論理的な一意の交差部分を表します。 たとえば、次のダイアグラムで示すキューブには、Source、Route、Time という 3 つのディメンションで編成された 2 つのメジャーを持つメジャー グループが 1 つ含まれています。  
  
 ![1 つのセルを示すキューブ図](../../analysis-services/multidimensional-models-olap-logical-cube-objects/media/as-cubeintro5.gif "1 つのセルを示すキューブ図")  
  
 このダイアグラムの 1 つの影付きセルは、次のメンバーの交差部分です。  
  
-   Route ディメンションの air メンバー  
  
-   Source ディメンションの Africa メンバー  
  
-   Time ディメンションの 4th quarter メンバー  
  
-   Packages メジャー  
  
## <a name="leaf-and-nonleaf-cells"></a>リーフ セルと非リーフ セル  
 キューブ内のセルの値は複数の方法で取得できます。 前の例では、セルの値直接から取得できます、キューブのファクト テーブルのセルの識別に使用されるすべてのメンバーがあるため*リーフ メンバー*です。 階層的にはリーフ メンバーに子メンバーはなく、通常はディメンション テーブルの 1 つのレコードを参照しています。 このようなセルと呼びます、*リーフ セル*です。  
  
 ただし、セルも特定できますを使用して*非リーフ メンバー*です。 非リーフ メンバーとは、1 つ以上の子メンバーを持っているメンバーです。 この場合、セルの値は通常、非リーフ メンバーに関連付けられている子メンバーの集計から取得されます。 たとえば、次のメンバーとディメンションの交差部分では、集計によって値が指定されるセルを参照します。  
  
-   Route ディメンションの air メンバー  
  
-   Source ディメンションの Africa メンバー  
  
-   Time ディメンションの 2nd half メンバー  
  
-   Packages メンバー  
  
 Time ディメンションの 2nd half メンバーは非リーフ メンバーです。 そのため、次のダイアグラムに示すように、2nd half メンバーに関連付けられているすべての値を集計する必要があります。  
  
 ![3 番目および第 4 四半期セル 2 nd half メンバー](../../analysis-services/multidimensional-models-olap-logical-cube-objects/media/as-cubeintro6.gif "第 3、第 4 四半期セル 2 nd half メンバー")  
  
 3rd quarter と 4th quarter の各メンバーの集計が合計であると仮定すると、指定したセルの値は、前のダイアグラムの影付きリーフ セルすべてを合計した 400 です。 指定されたセルと見なされます、セルの値は、その他のセルの集計から派生した、ため、*非リーフ セル*です。  
  
 カスタム メンバーだけでなくカスタム ロールアップやメンバー グループも使用しているメンバーのセルの値も、同様に取得されます。 ただし、計算されるメンバーのセルの値は、計算されるメンバーの定義に使用した多次元式 (MDX) 式に完全に基づいて取得されるため、場合によっては、実際のセル データは関係しないこともあります。 詳細については、次を参照してください。[親子ディメンションのカスタム ロールアップ演算子](../../analysis-services/multidimensional-models/parent-child-dimension-attributes-custom-rollup-operators.md)、[カスタム メンバー式の定義](../../analysis-services/multidimensional-models/attribute-properties-define-custom-member-formulas.md)、および[計算](../../analysis-services/multidimensional-models-olap-logical-cube-objects/calculations.md)です。  
  
## <a name="empty-cells"></a>空のセル  
 キューブ内のすべてのセルに値が必要なわけではありません。キューブには、データのない交差部分もあります。 このような交差部分は空のセルと呼ばれ、キューブ内にしばしば発生します。これは、キューブ内にメジャーを持つディメンション属性のすべての交差部分に、ファクト テーブル内の対応するレコードが含まれているとは限らないからです。 キューブ内のセルの合計数に対するキューブ内の空のセルの比率を頻繁に呼びます、*低密度*キューブのです。  
  
 たとえば、次のダイアグラムに示すキューブは、このトピックの他の例に似ていますが、 この例では、第 3 四半期の Africa または第 4 四半期の Australia への air による出荷が含まれていません。 これらのディメンションとメジャーの交差部分に対応するデータはファクト テーブルにありません。そのため、この交差部分にあるセルは空になります。  
  
 ![空のセルを示すキューブ図](../../analysis-services/multidimensional-models-olap-logical-cube-objects/media/as-cubeintro7.gif "空のセルを示すキューブ図")  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、空のセルはセルを特別な性質を持ちます。 空のセルは、相互結合、カウントなどの結果を非対称にできるため、多くの MDX 関数は、計算のために空のセルを無視する機能を提供しています。 詳細については、次を参照してください。[多次元式 & #40 です。MDX と #41 です。参照](../../mdx/multidimensional-expressions-mdx-reference.md)、および[重要な概念で MDX & #40 です。Analysis Services &#41;](../../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md).  
  
## <a name="security"></a>セキュリティ  
 セル データへのアクセスは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のロール レベルで管理され、MDX 式を使用して細かく制御できます。 詳細については、次を参照してください[データ &#40; をディメンションにカスタムのアクセスを許可。Analysis Services &#41;](../../analysis-services/multidimensional-models/grant-custom-access-to-dimension-data-analysis-services.md)、および[データ &#40; をセルにカスタムのアクセスを許可Analysis Services &#41;](../../analysis-services/multidimensional-models/grant-custom-access-to-cell-data-analysis-services.md).  
  
## <a name="see-also"></a>参照  
 [キューブのストレージと #40 です。Analysis Services - 多次元データ &#41;](../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-storage-analysis-services-multidimensional-data.md)   
 [集計と集計デザイン](../../analysis-services/multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)  
  
  

