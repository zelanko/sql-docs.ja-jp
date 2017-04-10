---
title: "式で使用される定数 (レポート ビルダーおよび SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b8ae650b-0f46-4848-b62b-15f8a40751b8
caps.latest.revision: 8
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 8
---
# 式で使用される定数 (レポート ビルダーおよび SSRS)
  定数は、リテラル テキストまたは定義済みのテキストです。 レポート プロセッサは定義済みの定数にアクセスできるので、このような定数を式に含めると、式が評価される前に、このような定数が表す値が式に代入されます。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## リテラル テキスト  
 式の中では、リテラル テキストは二重引用符で囲まれたテキストです。 テキストは、式の一部でない場合、二重引用符で囲まずにテキスト ボックスに直接入力することもできます。 テキスト ボックスの値が等号 (=) から始まっていなければ、テキストはリテラル テキストとして処理されます。 次の表に、式内のリテラル テキストの例をいくつか示します。  
  
|定数|表示テキスト|式のテキスト|  
|--------------|------------------|---------------------|  
|Report run at:|<\<Expr>>|`="Report run at: " & Globals!ExecutionTime`|  
|Adventure Works Cycles|Adventure Works Cycles|Adventure Works Cycles|  
|[角かっこで囲まれた表示テキスト]|\\[角かっこで囲まれた表示テキスト\\]|[角かっこで囲まれた表示テキスト]|  
  
## RDL 定数  
 レポート定義言語 (RDL) で定義されている定数は、式の中で使用できます。 **[式]** ダイアログ ボックスでは、特定の有効な値 (列挙型とも呼ばれます) のみを使用できるレポート プロパティの式を作成すると、定数が表示されます。 次の表に 2 つの例を示します。  
  
|プロパティ|Description|値|  
|--------------|-----------------|------------|  
|TextAlign|テキスト ボックス内でのテキストの配置に有効な値です。|General、Left、Center、Right|  
|BorderStyle|レポートに追加された線に有効な値です。|Default、None、Dotted、Dashed、Solid、Double、DashDot、DashDotdot|  
  
## Visual Basic 定数  
 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] ランタイム ライブラリで定義されている定数を、式の中で使用できます。 たとえば、定数 **DateInterval.Day**を使用できます。 2008 年 1 月 10 日の場合、次の関数を使用すると、数値 10 が返されます。  
  
 `=DatePart("d",Globals!ExecutionTime)`  
  
## CLR 定数  
 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] の共通言語ランタイム (CLR) クラスで定義されている定数は、式の中で使用できます。 次の表に、システム定義色の例を示します。  
  
|定数|Description|  
|--------------|-----------------|  
|MistyRose|背景色に基づいたレポート プロパティの式を作成する場合は、色を名前で指定できます。 有効な名前は、 **[式]** ダイアログ ボックスに表示されます。|  
  
## 参照  
 [[式] ダイアログ ボックス](../Topic/Expression%20Dialog%20Box.md)   
 [式 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)   
 [式の例 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [式で使用されるデータ型 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [[式] ダイアログ ボックス &#40;レポート ビルダー&#41;](../Topic/Expression%20Dialog%20Box%20\(Report%20Builder\).md)  
  
  