---
title: "クエリ スコープのセル計算 (MDX) を作成する |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WITH keyword
- query-scoped cell calculations [MDX]
ms.assetid: 45987daa-4400-41e9-add7-2428fd75709b
caps.latest.revision: "30"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: d6b38d88d6a9bf5ba180a9023a962199633a6a4b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="mdx-cell-calculations---query-scoped-cell-calculations"></a>クエリ スコープのセル計算の MDX セル計算
  計算されるセルをクエリのコンテキストの中で記述するには、多次元式 (MDX) の **WITH** キーワードを使用します。 **WITH** キーワードの構文は、以下のとおりです。  
  
```  
WITH CELL CALCULATION Cube_Name.CellCalc_Identifier  String_Expression  
```  
  
 `CellCalc_Identifier` の値は、計算されるセルの名前です。 `String_Expression` の値には、直交する 1 次元の MDX セット式の一覧を指定します。 それぞれの式は次の表に示されているカテゴリのいずれかに解決する必要があります。  
  
|カテゴリ|Description|  
|--------------|-----------------|  
|空セット|空セットに解決される MDX セット式。 この場合、計算されるセルのスコープはキューブ全体です。|  
|単一メンバー セット|1 つのメンバーに解決される MDX セット式。|  
|レベル メンバーのセット|単一レベルのメンバーに解決される MDX セット式。 このようなセット式の例として、 *Level_Expression*.**Members** MDX 関数があります。 計算されるメンバーを含めるには、*Level_Expression*.**AllMembers** MDX 関数を使用します。 詳細については、「[AllMembers (MDX)](../../../mdx/allmembers-mdx.md)」を参照してください。|  
|子孫のセット|指定したメンバーの子孫に解決される MDX セット式。 このようなセット式の例として、**Descendants**(*Member_Expression*, *Level_Expresion*, *Desc_Flag*) MDX 関数があります。 詳細については、「[Descendants (MDX)](../../../mdx/descendants-mdx.md)」を参照してください。|  
  
 `String_Expression` 引数でディメンションが記述されていない場合、MDX は計算サブキューブの構築のためにすべてのメンバーが含まれていると想定します。 したがって、 `String_Expression` 引数が NULL の場合、計算されるセルの定義はキューブ全体に適用されます。  
  
 `MDX_Expression` 引数には、 `String_Expression` 引数で定義したすべてのセルのセル値に評価される MDX 式を指定します。  
  
## <a name="additional-considerations"></a>その他の注意点  
 **CONDITION** プロパティによって指定された計算条件は、MDX によって一度だけ処理されます。 このように一度だけの処理を行うことにより、複数の計算されるセルの定義を評価する場合、特に計算されるセルがキューブ パス間で重複している場合のパフォーマンスが向上します。  
  
 この一度だけの処理がいつ行われるかは、計算されるセルの定義の作成スコープによって異なります。  
  
-   キューブの一部としてグローバル スコープで作成した計算条件は、MDX によってそのキューブの処理時に処理されます。 キューブ内でセルがなんらかの方法で修正され、そのセルが計算されるセルの定義の計算サブキューブに含まれている場合は、キューブが再処理されるまで正確な計算条件が得られないことがあります。 たとえば、書き戻しによってセルの修正が発生する場合があります。 計算条件は、キューブと共に再処理されます。  
  
-   セッション スコープで作成された計算条件は、MDX によってセッション中のステートメントの実行時に処理されます。 グローバルに作成された計算されるセルの定義と同様に、この種の計算されるセルの定義の場合も、セルが修正されると正確な計算条件が得られないことがあります。  
  
-   クエリ スコープで作成された計算条件は、MDX によってクエリの実行時に処理されます。 この場合もセルの修正に関する問題が当てはまりますが、MDX クエリの実行は処理時間が少ないため、データ待機時間に伴う問題は最小限に抑えられます。  
  
 一方、計算式は、計算されるセルの定義に含まれるセルを伴うキューブに対して MDX クエリが実行されるたびに MDX によって処理されます。 この処理は、作成スコープに関係なく行われます。  
  
## <a name="see-also"></a>参照  
 [CREATE CELL CALCULATION ステートメント (MDX)](../../../mdx/mdx-data-definition-create-cell-calculation.md)  
  
  
