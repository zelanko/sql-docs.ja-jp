---
title: "avg 関数 (XQuery) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: xquery
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- fn:avg function
- avg function [XQuery]
ms.assetid: 0cc60267-3c56-4a88-8ad7-bb07f0255d56
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ee1d24bc4b28b7a041baa42ac829424e5daa6f8b
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="aggregate-functions---avg"></a>集計関数の avg
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  一連の数値の平均値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
fn:avg($arg as xdt:anyAtomicType*) as xdt:anyAtomicType?  
```  
  
## <a name="arguments"></a>引数  
 *$arg*  
 平均値を計算するアトミック値のシーケンス。  
  
## <a name="remarks"></a>解説  
 渡されるアトミック値のすべての種類**avg()** 3 つの組み込み数値基本型または xdt:untypedAtomic のただ 1 つのサブタイプである必要があります。 これらの型を混在させることはできません。 xdt:untypedAtomic 型の値は、xs:double として扱われます。 結果**avg()** xdt:untypedAtomic の場合は xs:double など、渡された型の基本型を受け取ります。  
  
 入力が静的に空の場合、空になることが暗黙に示され、静的エラーが発生します。  
  
 **Avg()**関数を計算する数値の平均値を返します。 例:  
  
 **sum(** *$arg* **) div count(** *$arg* **)**  
  
 場合*$arg* 、空のシーケンスは、空のシーケンスが返されます。  
  
 If an xdt:untypedAtomic value cannot be cast to xs:double, the value is disregarded in the input sequence, *$arg*.  
  
 他のすべての場合は、関数から静的エラーが返されます。  
  
## <a name="examples"></a>使用例  
 このトピックでは、さまざまなに格納されている XML インスタンスに対して XQuery の例は、 **xml** AdventureWorks データベース内の列を入力します。  
  
### <a name="a-using-the-avg-xquery-function-to-find-work-center-locations-in-the-manufacturing-process-in-which-labor-hours-are-greater-than-the-average-for-all-work-center-locations"></a>A. avg() XQuery 関数を使用した、製造プロセス中のワーク センターの場所全体での平均労働時間よりも長いワーク センターの検索  
 指定したクエリを書き直すことができます[min 関数 (XQuery)](../xquery/aggregate-functions-min.md)を使用する、 **avg()**関数。  
  
## <a name="implementation-limitations"></a>実装の制限事項  
 制限事項を次に示します。  
  
-   **Avg()**関数では、すべての整数値を xs:decimal にマップします。  
  
-   **Avg()** xs:duration 型の値に対して関数がサポートされていません。  
  
-   基本データ型の境界を超えて複数の型が混在するシーケンスはサポートされません。  
  
## <a name="see-also"></a>参照  
 [xml データ型に対する XQuery 関数](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
