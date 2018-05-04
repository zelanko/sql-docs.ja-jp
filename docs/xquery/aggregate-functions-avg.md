---
title: avg 関数 (XQuery) |Microsoft ドキュメント
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: sql
ms.service: ''
ms.component: xquery
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- fn:avg function
- avg function [XQuery]
ms.assetid: 0cc60267-3c56-4a88-8ad7-bb07f0255d56
caps.latest.revision: 29
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 4f3c3acc233552cae8f3237e38ef3b4328b4eee5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
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
  
 **Avg()** 関数を計算する数値の平均値を返します。 以下に例を示します。  
  
 **sum (** *$arg* **) div カウント (** *$arg* **)**  
  
 場合 *$arg* 、空のシーケンスは、空のシーケンスが返されます。  
  
 Xdt:untypedAtomic 値は、xs:double にキャストすることはできない場合、入力シーケンスで値が無視されます。 *$arg*です。  
  
 他のすべての場合は、関数から静的エラーが返されます。  
  
## <a name="examples"></a>使用例  
 このトピックでは、さまざまなに格納されている XML インスタンスに対して XQuery の例は、 **xml** AdventureWorks データベース内の列を入力します。  
  
### <a name="a-using-the-avg-xquery-function-to-find-work-center-locations-in-the-manufacturing-process-in-which-labor-hours-are-greater-than-the-average-for-all-work-center-locations"></a>A. avg() XQuery 関数を使用した、製造プロセス中のワーク センターの場所全体での平均労働時間よりも長いワーク センターの検索  
 指定したクエリを書き直すことができます[min 関数 (XQuery)](../xquery/aggregate-functions-min.md)を使用する、 **avg()** 関数。  
  
## <a name="implementation-limitations"></a>実装の制限事項  
 制限事項を次に示します。  
  
-   **Avg()** 関数では、すべての整数値を xs:decimal にマップします。  
  
-   **Avg()** xs:duration 型の値に対して関数がサポートされていません。  
  
-   基本データ型の境界を超えて複数の型が混在するシーケンスはサポートされません。  
  
## <a name="see-also"></a>参照  
 [xml データ型に対する XQuery 関数](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
