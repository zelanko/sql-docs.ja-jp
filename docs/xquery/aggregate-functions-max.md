---
title: max 関数 (XQuery) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/09/2017
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
- max function [XQuery]
- fn:max function
ms.assetid: 5ee625c0-044a-4cda-b210-02b64e619d65
caps.latest.revision: 29
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: a53b02bc682bf7b3c918a02d5a16dc326ca3a594
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="aggregate-functions---max"></a>集計関数の max
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  アトミック値のシーケンスを返します *$arg*値を持つしたよりも大きい他のすべての項目を 1 つです。  
  
## <a name="syntax"></a>構文  
  
```  
  
fn:max($arg as xdt:anyAtomicType*) as xdt:anyAtomicType?  
```  
  
## <a name="arguments"></a>引数  
 *$arg*  
 最大値の取得元になるアトミック値のシーケンス。  
  
## <a name="remarks"></a>解説  
 すべての種類に渡されるアトミック値の**max()** 同じ基本型のサブタイプである必要があります。 受け付けられるベースの型をサポートする型は、 **gt**操作します。 この型には、3 つの組み込み数値基本データ型、date/time 基本データ型、xs:string、xs:boolean、および xdt:untypedAtomic が含まれます。 xdt:untypedAtomic 型の値は、xs:double にキャストされます。 これらの型の混在がある場合、またはその他の種類の他の値が渡された場合は、静的エラーが発生します。  
  
 結果**max()** xdt:untypedAtomic の場合は xs:double など、渡された型の基本型を受け取ります。 入力が静的に空の場合は、結果が暗黙的に空になり、静的エラーが生成されます。  
  
 **Max()** 関数が入力シーケンス内の他のよりも大きいシーケンス内の 1 つの値を返します。 xs:string 値の場合は、既定の Unicode コードポイント照合順序が使用されます。 Xdt:untypedAtomic 値は、xs:double にキャストすることはできない場合、入力シーケンスで値が無視されます。 *$arg*です。 入力が、動的に計算された空のシーケンスである場合は、空のシーケンスが返されます。  
  
## <a name="examples"></a>使用例  
 このトピックでは、さまざまなに格納されている XML インスタンスに対して XQuery の例は、 **xml**内の列を入力、[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]データベース。  
  
### <a name="a-using-the-max-xquery-function-to-find-work-center-locations-in-the-manufacturing-process-that-have-the-most-labor-hours"></a>A. max() XQuery 関数を使用した、製造プロセス内で労働時間が最も長いワーク センターの場所の検索  
 指定したクエリ[min 関数 (XQuery)](../xquery/aggregate-functions-min.md)を使用して書き換えることができます、 **max()** 関数。  
  
## <a name="implementation-limitations"></a>実装の制限事項  
 制限事項を次に示します。  
  
-   **Max (**) 関数では、すべての整数値を xs:decimal にマップします。  
  
-   **Max()** xs:duration 型の値に対して関数がサポートされていません。  
  
-   基本データ型の境界を超えて複数の型が混在するシーケンスはサポートされません。  
  
-   照合順序を指定する構文オプションはサポートされません。  
  
## <a name="see-also"></a>参照  
 [xml データ型に対する XQuery 関数](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
