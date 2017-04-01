---
title: "DRILLTHROUGH を使用したソース データの取得 (MDX) | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DRILLTHROUGH ステートメント"
  - "データの取得"
  - "クエリ [MDX], DRILLTHROUGH ステートメント"
  - "データ取得 [MDX]"
ms.assetid: fe0ab170-25a9-45a8-a377-f71a67f77018
caps.latest.revision: 30
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# DRILLTHROUGH を使用したソース データの取得 (MDX)
  多次元式 (MDX) では、キューブ セルのソース データから行セットを取得するために [DRILLTHROUGH](../Topic/DRILLTHROUGH%20Statement%20\(MDX\).md) ステートメントを使用します。  
  
 キューブに対して **DRILLTHROUGH** ステートメントを実行するには、そのキューブに対するドリルスルー アクションを定義する必要があります。 ドリルスルー アクションを定義するには、[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] のキューブ デザイナーの **[アクション]** ペインで、ツール バーの **[新しいドリルスルー アクション]** をクリックします。 新しいドリルスルー アクションでは、アクションの名前、対象、条件を指定し、**DRILLTHROUGH** ステートメントによって返される列を指定します。  
  
## DRILLTHROUGH ステートメントの構文  
 **DRILLTHROUGH** ステートメントの構文は、以下のとおりです。  
  
```  
<drillthrough> ::= DRILLTHROUGH [<Max_Rows>] [<First_Rowset>] <MDX select> [<Return_Columns>]  
   < Max_Rows> ::= MAXROWS <positive number>  
   <First_Rowset> ::= FIRSTROWSET <positive number>  
   <Return_Columns> ::= RETURN <member or attribute> [, <member or attribute>]  
```  
  
 **SELECT** 句は、取得対象のソース データが入っているキューブ セルを識別します。 この **SELECT** 句は MDX の通常の **SELECT** ステートメントとほぼ同じですが、**SELECT** 句の場合、それぞれの軸上で 1 つのメンバーだけを指定できます。 1 つの軸で複数のメンバーが指定されている場合、エラーが発生します。  
  
 構文 `<Max_Rows>` は、返されるそれぞれの行セットにおける行の最大数を指定します。 データ ソースとの接続に使われる OLE DB プロバイダーが **DBPROP_MAXROWS** をサポートしない場合、`<Max_Rows>` の設定は無視されます。  
  
 構文 `<First_Rowset>` は、どのパーティションの行セットが最初に返されるかを識別します。  
  
 構文 `<Return_Columns>` は、基になるデータベースのどの列が返されるかを識別します。  
  
## DRILLTHROUGH ステートメントの例  
 以下の例は、**DRILLTHROUGH** ステートメントの使用方法を示しています。 この例の DRILLTHROUGH ステートメントは、Stores ディメンション (スライサー軸) 上の Store、Product、Time ディメンションのリーフを照会して、部門メジャー グループ、部門 ID、従業員の名前を返します。  
  
```  
DRILLTHROUGH  
Select {Leaves(Store), Leaves(Product), Leaves(Time),*} on 0  
From Stores  
RETURN [Department MeasureGroup].[Department Id], [Employee].[First Name]  
```  
  
## 参照  
 [データの操作 &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/manipulating-data-mdx.md)  
  
  