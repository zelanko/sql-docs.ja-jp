---
title: "MDX および DAX での VBA 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/30/2018
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 420452fd-9507-4093-8857-71d3e70d96cc
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: 6356a6c841072490e10f9c32933606010ce0b9f9
ms.sourcegitcommit: b4fd145c27bc60a94e9ee6cf749ce75420562e6b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2018
---
# <a name="vba-functions-in-mdx-and-dax"></a>MDX および DAX での VBA 関数
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  このドキュメントには、交差で使用できるすべての VBA 関数の参照が含まれています[アプリケーション関数の Visual Basic](https://msdn.microsoft.com/vba/language-reference-vba/articles/functions-visual-basic-for-applications) MDX でサポートされている; も、リストでは、DAX 言語で同等の機能がある場合に、ノートが含まれています.  
  
## <a name="visual-basic-for-applications-functions-reference"></a>Visual Basic for Applications 関数リファレンス  
  
|関数名|Supported|注|  
|-------------------|---------------|-----------|  
|Abs|DAX、MDX||  
|Array|サポートされていません||  
|Asc|MDX のみ||  
|AscW|MDX のみ||  
|Atn|MDX のみ||  
|CallByName|サポートされていません||  
|CBool|MDX のみ||  
|CByte|MDX のみ||  
|CCur|MDX のみ||  
|CDate|MDX のみ||  
|CDbl|MDX のみ||  
|CDec|MDX のみ||  
|Choose|MDX のみ||  
|Chr|MDX のみ||  
|CInt|MDX のみ||  
|CLng|MDX のみ||  
|CLngLng|サポートされていません||  
|CLngPtr|サポートされていません||  
|Command|サポートされていません||  
|Cos|MDX のみ||  
|CreateObject|サポートされていません||  
|CSng|MDX のみ||  
|CStr|MDX のみ||  
|CurDir|サポートされていません||  
|CVar|MDX のみ||  
|CVErr|サポートされていません||  
|日付|MDX のみ|**警告**DAX が同じで別の関数を実装する名前は、DATE (Year, Month, Day) 関数は、指定された引数から日付型の値を生成するために使用|  
|DateAdd|MDX のみ|**警告**DAX が同じで別の関数を実装する名前; DATEADD (\<日付 >、< number_of_intervals >\<間隔 >) の数で指定された日付をシフトするために使用されている関数の間隔を指定|  
|DateDiff]|MDX のみ||  
|DatePart|MDX のみ||  
|DateSerial|MDX のみ||  
|DateValue]|DAX、MDX||  
|日|DAX、MDX||  
|DDB|MDX のみ||  
|Dir|サポートされていません||  
|DoEvents|サポートされていません||  
|Environ|サポートされていません||  
|EOF|サポートされていません||  
|[エラー]|サポートされていません||  
|Exp|DAX、MDX||  
|FileAttr|サポートされていません||  
|FileDateTime|サポートされていません||  
|FileLen|サポートされていません||  
|[フィルター]|サポートされていません|**警告**MDX が同じ名前の別の関数を実装する以外の場合は、FILTER (Set_Expression, Logical_Expression) 関数には、指定された引数から、検索条件に基づいて、指定されたセットをフィルター処理を実行した結果セットが返されます。<br /><br /> **警告**DAX が同じで別の関数を実装する名前の FILTER (\<テーブル >、\<フィルター >) を別のテーブルまたは指定された引数から式のサブセットを表すテーブルを返す関数|  
|Fix|MDX のみ||  
|Format (Visual Basic for Applications)|DAX、MDX||  
|FormatCurrency|サポートされていません||  
|FormatDateTime|サポートされていません||  
|FormatNumber|サポートされていません||  
|FormatPercent|サポートされていません||  
|FreeFile|サポートされていません||  
|FV|MDX のみ||  
|GetAllSettings|サポートされていません||  
|GetAttr|サポートされていません||  
|GetObject|サポートされていません||  
|GetSetting|サポートされていません||  
|Hex|MDX のみ||  
|Hour|DAX、MDX||  
|Iif|MDX のみ|**警告**DAX が名前を持つ同様の機能を実装する: IF (logical_test、value_if_true, value_if_false) 関数です。|  
|IMEStatus|サポートされていません||  
|入力|サポートされていません||  
|InputBox|サポートされていません||  
|InStr|MDX のみ||  
|InStrRev|サポートされていません||  
|Int|DAX、MDX||  
|IPmt|MDX のみ||  
|IRR|MDX のみ||  
|IsArray|MDX のみ||  
|IsDateMDX のみ||  
|IsEmpty|MDX のみ||  
|IsError|DAX、MDX||  
|IsMissing|MDX のみ||  
|IsNull|MDX のみ||  
|IsNumeric|MDX のみ||  
|IsObject|サポートされていません||  
|Join|サポートされていません||  
|LBound|サポートされていません||  
|LCase|MDX のみ||  
|[左]|DAX、MDX||  
|Len|DAX、MDX||  
|Loc|サポートされていません||  
|LOF|サポートされていません||  
|Log|MDX のみ|**重要な**DAX が同じで別の関数を実装する名前は、ログ (番号が、基本) 関数です。 この関数は、指定された引数からの指定された数を底とする対数を返します。|  
|LTrim|MDX のみ||  
|MacID|サポートされていません||  
|MacScript|サポートされていません||  
|Mid|DAX、MDX||  
|Minute|DAX、MDX||  
|MIRR|MDX のみ||  
|Month|DAX、MDX||  
|MonthName|サポートされていません||  
|MsgBox|サポートされていません||  
|[今]|DAX、MDX||  
|[期間]|MDX のみ||  
|NPV|MDX のみ||  
|Oct|MDX のみ||  
|パーティション|MDX のみ||  
|Pmt|MDX のみ||  
|PPmt|MDX のみ||  
|PV|MDX のみ||  
|QBColor|MDX のみ||  
|Rate|MDX のみ||  
|[置換]|サポートされていません||  
|RGB|MDX のみ||  
|[右]|DAX、MDX||  
|Rnd|MDX のみ||  
|四捨五入|DAX、MDX||  
|RTrim|MDX のみ||  
|第 2 週|DAX、MDX||  
|Seek|サポートされていません||  
|Sgn|DAX、MDX||  
|Shell|サポートされていません||  
|Sin|MDX のみ||  
|SLN|MDX のみ||  
|Space|MDX のみ||  
|Spc|サポートされていません||  
|分割|サポートされていません||  
|Sqr|MDX のみ||  
|Str|MDX のみ||  
|StrComp|MDX のみ||  
|StrConv|MDX のみ||  
|String]|MDX のみ||  
|StrReverse|サポートされていません||  
|スイッチ|MDX のみ||  
|SYD|MDX のみ||  
|タブ|サポートされていません||  
|Tan|MDX のみ||  
|[時刻]|サポートされていません||  
|Timer|MDX のみ||  
|TimeSerial|MDX のみ||  
|TimeValue|DAX、MDX||  
|トリム]|DAX、MDX||  
|TypeName|MDX のみ||  
|UBound|サポートされていません||  
|UCase|MDX のみ||  
|Val|MDX のみ||  
|VarType|サポートされていません||  
|Weekday|DAX、MDX||  
|WeekdayName|サポートされていません||  
|年|DAX、MDX||  
  
  
