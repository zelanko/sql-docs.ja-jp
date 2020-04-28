---
title: round 関数 (XQuery) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- fn:round function
- round function [XQuery]
ms.assetid: 320b572f-bd5b-4055-95a6-dec5718c0041
author: rothja
ms.author: jroth
ms.openlocfilehash: 1927d6e483683699196cfc7e87928f27bf23446a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67946545"
---
# <a name="numeric-values-functions---round"></a>数値関数 - round
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  引数に最も近く、小数部分を持たない数値を返します。 そのような数値が複数ある場合は、正の無限大に最も近いものが返されます。 次に例を示します。  
  
 引数が2.5 の場合、 **round ()** は3を返します。  
  
 引数が2.4999 の場合、 **round ()** は2を返します。  
  
 引数が-2.5 の場合、 **round ()** は-2 を返します。  
  
 引数が空のシーケンスの場合、 **round ()** は空のシーケンスを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
fn:round ( $arg as numeric?) as numeric?  
```  
  
## <a name="arguments"></a>引数  
 *$arg*  
 関数が適用される番号。  
  
## <a name="remarks"></a>Remarks  
 *$Arg*の型が、 **xs: float**、 **xs: double**、または**xs: decimal**の3つの数値基本データ型のいずれかである場合、戻り値の型は *$arg*の型と同じになります。 *$Arg*の型が数値型の1つから派生した型である場合、戻り値の型は基本数値型です。  
  
 **Fn: floor**、 **fn: シーリング**、または**fn: round**関数への入力が**xdt: untypedAtomic**で、型指定されていないデータの場合、 **xs: double**に暗黙的にキャストされます。  
  
 その他の型のデータが入力されると、静的エラーが生成されます。  
  
## <a name="examples"></a>使用例  
 このトピックでは、AdventureWorks データベースのさまざまな**xml**型の列に格納されている xml インスタンスに対して XQuery の例を示します。  
  
 **Round ()** xquery 関数には、[天井関数 (xquery)](../xquery/numeric-values-functions-ceiling.md)の working サンプルを使用できます。 クエリの**切り上げ ()** 関数を**round ()** 関数に置き換えるだけで済みます。  
  
## <a name="implementation-limitations"></a>実装の制限事項  
 制限事項は次のとおりです。  
  
-   **Round ()** 関数は、整数値を xs: decimal にマップします。  
  
-   -0.5 e0 から-0e0 までの xs: double および xs: float 値の**round ()** 関数は、-0e0 ではなく0e0 にマップされます。  
  
## <a name="see-also"></a>参照  
 [floor 関数 &#40;XQuery&#41;](../xquery/numeric-values-functions-floor.md)   
 [シーリング関数 &#40;XQuery&#41;](../xquery/numeric-values-functions-ceiling.md)  
  
  
