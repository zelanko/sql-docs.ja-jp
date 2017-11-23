---
title: "floor 関数 (XQuery) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/09/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
dev_langs: XML
helpviewer_keywords:
- floor function [XQuery]
- fn:floor function
ms.assetid: 4ace57dd-b66e-4b60-a2b9-a1b0f1a0831d
caps.latest.revision: "27"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1366a4b3a5f9f8793999f50c7d55b9528dfee19d
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="numeric-values-functions---floor"></a>数値の値関数、floor します。
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  引数の値を超えず、小数部のない最も大きな数値を返します。 引数が空のシーケンスの場合は、空のシーケンスを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
fn:floor ($arg as numeric?) as numeric?  
```  
  
## <a name="arguments"></a>引数  
 *$arg*  
 関数を適用する数値。  
  
## <a name="remarks"></a>解説  
 場合の種類*$arg*は 3 つの数値基本型の 1 つ**xs:float**、 **xs:double**、または**xs:decimal**、戻り値の型と同じ、*$arg*型です。 場合の種類*$arg*数値型のいずれかから派生した型は、戻り値の型は、基本の数値型。  
  
 Fn:floor、fn:ceiling、または fn:round 関数への入力が場合**xdt:untypedAtomic**、型指定されていないデータは、暗黙的にキャストされた**xs:double**です。 その他の型のデータが入力されると、静的エラーが生成されます。  
  
## <a name="examples"></a>使用例  
 このトピックでは、さまざまなに格納されている XML インスタンスに対して XQuery の例は、 **xml** AdventureWorks サンプル データベース内の列を入力します。  
  
 作業用サンプルを使用することができます、 [ceiling 関数 (XQuery)](../xquery/numeric-values-functions-ceiling.md)の**floor()** XQuery 関数。 置換を行うには必要なは、 **ceiling()**と、クエリの関数、 **floor()**関数。  
  
## <a name="implementation-limitations"></a>実装の制限事項  
 制限事項を次に示します。  
  
-   **Floor()**関数では、すべての整数値を xs:decimal にマップします。  
  
## <a name="see-also"></a>参照  
 [ceiling 関数と #40 です。XQuery と #41 です。](../xquery/numeric-values-functions-ceiling.md)   
 [round 関数 &#40;です。XQuery と #41 です。](../xquery/numeric-values-functions-round.md)   
 [xml データ型に対する XQuery 関数](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
