---
title: round 関数 (XQuery) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql
ms.component: xquery
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- fn:round function
- round function [XQuery]
ms.assetid: 320b572f-bd5b-4055-95a6-dec5718c0041
caps.latest.revision: 29
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 69c9e11d9cb6dda3aa50a2d49e3eb9c55b99a57b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "33078129"
---
# <a name="numeric-values-functions---round"></a>数値の値関数の round
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  引数に最も近く、小数部分を持たない数値を返します。 そのような数値が複数ある場合、正の無限大に最も近い数値が返されます。 以下に例を示します。  
  
 引数が 2.5 の場合**round()** 3 が返されます。  
  
 引数がある場合、2.4999 場合**round()** 2 を返します。  
  
 場合は、引数が-2.5、 **round()** -2 を返します。  
  
 引数が空のシーケンスの場合**round()** 空のシーケンスを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
fn:round ( $arg as numeric?) as numeric?  
```  
  
## <a name="arguments"></a>引数  
 *$arg*  
 関数を適用する数値。  
  
## <a name="remarks"></a>解説  
 場合の種類 *$arg*は 3 つの数値基本型の 1 つ**xs:float**、 **xs:double**、または**xs:decimal**、戻り値の型と同じ、*$arg*型です。 場合の種類 *$arg*数値型のいずれかから派生した型は、戻り値の型は、基本の数値型。  
  
 場合に入力する、 **fn:floor**、 **fn:ceiling**、または**fn:round**関数は**xdt:untypedAtomic**、型指定されていないデータは、暗黙的にキャストされます**xs:double**です。  
  
 その他の型のデータが入力されると、静的エラーが生成されます。  
  
## <a name="examples"></a>使用例  
 このトピックでは、さまざまなに格納されている XML インスタンスに対して XQuery の例**xml** AdventureWorks データベース内の列を入力します。  
  
 作業用サンプルを使用することができます、 [ceiling 関数 (XQuery)](../xquery/numeric-values-functions-ceiling.md)の**round()** XQuery 関数。 置換を行うには必要なは、 **ceiling()** と、クエリの関数、 **round()** 関数。  
  
## <a name="implementation-limitations"></a>実装の制限事項  
 制限事項を次に示します。  
  
-   **Round()** 関数では、整数値を xs:decimal にマップします。  
  
-   **Round()** xs:double 値および xs:float 値 - 0.5e0 と 0e0 の関数ではなく - 0e0 0e0 にマップされます。  
  
## <a name="see-also"></a>参照  
 [floor 関数&#40;XQuery&#41;](../xquery/numeric-values-functions-floor.md)   
 [ceiling 関数&#40;XQuery&#41;](../xquery/numeric-values-functions-ceiling.md)  
  
  
