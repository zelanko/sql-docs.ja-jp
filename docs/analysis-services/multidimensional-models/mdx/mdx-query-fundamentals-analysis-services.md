---
title: "MDX クエリの基礎 (Analysis Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/13/2017"
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
  - "ステートメント [MDX]"
  - "ステートメントである多次元式 [Analysis Services]"
  - "多次元式 [Analysis Services], クエリ"
  - "[Analysis Services] ダイアログ ボックスの MDX ステートメント"
  - "MDX クエリ [Analysis Services]"
  - "MDX [Analysis Services], クエリ"
  - "クエリ [MDX]"
ms.assetid: a560383b-bb58-472e-95f5-65d03d8ea08b
caps.latest.revision: 31
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 30
---
# MDX クエリの基礎 (Analysis Services)
  多次元式 (MDX) を使用すれば、多次元オブジェクト (たとえばキューブ) をクエリして、キューブ データが格納された多次元セル セットを返すことができます。 このトピックとサブトピックでは、MDX クエリの概要を説明します。  
  
 以下のトピックでは、MDX クエリとクエリが作成するセル セットについて、および基本的な MDX 構文の詳細について説明します。  
  
> [!NOTE]  
>  MDX クエリおよび計算に関連するパフォーマンスの問題の詳細については、「[SQL Server 2005 Analysis Services パフォーマンス ガイド](http://go.microsoft.com/fwlink/?LinkId=81621)」の「効率的な MDX の記述」セクションを参照してください。  
  
## このセクションの内容  
  
|トピック|Description|  
|-----------|-----------------|  
|[MDX の基本的なクエリ &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/the-basic-mdx-query-mdx.md)|MDX SELECT ステートメントの基本的な構文について説明します。|  
|[クエリ軸とスライサー軸によるクエリの制限 &#40;MDX&#41;](../Topic/Restricting%20the%20Query%20with%20Query%20and%20Slicer%20Axes%20\(MDX\).md)|クエリ軸とスライサー軸、およびそれらを指定する方法について説明します。|  
|[クエリ内のキューブ コンテキストの確立 &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/establishing-cube-context-in-a-query-mdx.md)|MDX SELECT ステートメントでの FROM 句の用途を説明します。|  
|[MDX での名前付きセットの作成 &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/building-named-sets-in-mdx-mdx.md)|MDX での名前付きセットの用途と、名前付きセットを MDX クエリ内で作成および使用するために必要なテクニックについて説明します。|  
|[MDX での計算されるメンバーの作成 &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/building-calculated-members-in-mdx-mdx.md)|MDX での計算されるメンバーに関する情報と、計算されるメンバーを MDX 式内で作成および使用するために必要なテクニックについて説明します。|  
|[MDX でのセル計算の作成 &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/building-cell-calculations-in-mdx-mdx.md)|計算されるセルを作成および使用する処理の詳細について説明します。|  
|[プロパティ値の作成および使用 &#40;MDX&#41;](../Topic/Creating%20and%20Using%20Property%20Values%20\(MDX\).md)|ディメンション、レベル、メンバー、およびセルの各プロパティの作成時および使用時の処理の詳細について説明します。|  
|[データの操作 &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/manipulating-data-mdx.md)|ドリルスルーとロールアップを使ったデータ操作の基礎について、および MDX でのパス順序と解決順序について説明します。|  
|[データの変更 &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/modifying-data-mdx.md)|書き戻しを使って多次元データを一時的または永続的に変更する方法について説明します。|  
|[変数とパラメーターの使用 &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/using-variables-and-parameters-mdx.md)|MDX クエリ内での変数およびパラメーターの使用方法について説明します。|  
  
## 参照  
 [多次元式 &#40;MDX&#41; リファレンス](../../../mdx/multidimensional-expressions-mdx-reference.md)  
  
  