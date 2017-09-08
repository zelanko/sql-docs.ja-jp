---
title: "distinct-values 関数 (XQuery) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/09/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- distinct-values function
- fn:distinct-values function
ms.assetid: f4c2bb53-2bec-4f1a-9c00-cf997fb7ae5b
caps.latest.revision: 26
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 94650b355d0431b66103237b019dff01fedbc0e9
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="functions-on-sequences---distinct-values"></a>シーケンスの個別の値に使用する関数
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  重複する値で指定されたシーケンスからの削除*$arg*です。 場合*$arg* 、空のシーケンスは、空のシーケンスを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
fn:distinct-values($arg as xdt:anyAtomicType*) as xdt:anyAtomicType*  
```  
  
## <a name="arguments"></a>引数  
 *$arg*  
 アトミック値のシーケンス。  
  
## <a name="remarks"></a>解説  
 すべての種類に渡されるアトミック値の**distinct-values()**同じ基本型のサブタイプである必要があります。 受け付けられるベースの型をサポートする型は、 **eq**操作します。 この型には、3 つの組み込み数値基本データ型、date/time 基本データ型、xs:string、xs:boolean、および xdt:untypedAtomic が含まれます。 xdt:untypedAtomic 型の値は、xs:string にキャストされます。 これらの型が混在している場合、または他の型の他の値が渡された場合は、静的エラーが発生します。  
  
 結果**distinct-values()**元 cardinality xs:string xdt:untypedAtomic の場合など、渡された型の基本型を受け取ります。 入力が静的に空の場合は、結果が暗黙的に空になり、静的エラーが生成されます。  
  
 xs:string 型の値は、XQuery の既定の Unicode コードポイント照合順序と比較されます。  
  
## <a name="examples"></a>使用例  
 このトピックでは、さまざまなに格納されている XML インスタンスに対して XQuery の例は、 **xml** AdventureWorks データベース内の列を入力します。  
  
### <a name="a-using-the-distinct-values-function-to-remove-duplicate-values-from-the-sequence"></a>A. distinct-values() 関数を使用てシーケンス内の重複する値を削除する  
 この例では、電話番号を格納している XML インスタンスに割り当てられた、 **xml**型の変数です。 この変数を使用してに対して指定した XQuery、 **distinct-values()**重複が含まれていないの電話番号の一覧をコンパイルする関数。  
  
```  
declare @x xml  
set @x = '<PhoneNumbers>  
 <Number>111-111-1111</Number>  
 <Number>111-111-1111</Number>  
 <Number>222-222-2222</Number>  
</PhoneNumbers>'  
-- 1st select  
select @x.query('  
  distinct-values( data(/PhoneNumbers/Number) )  
') as result  
```  
  
 結果を次に示します。  
  
```  
111-111-1111 222-222-2222    
```  
  
 次のクエリでは、一連の数値 (1, 1, 2) に渡して、 **distinct-values()**関数。 関数は、シーケンス内の重複する値を削除し、結果として得られた 2 つの値を返します。  
  
```  
declare @x xml  
set @x = ''  
select @x.query('  
  distinct-values((1, 1, 2))  
') as result  
```  
  
 クエリは 1 2 を返します。  
  
### <a name="implementation-limitations"></a>実装の制限事項  
 制限事項を次に示します。  
  
-   **Distinct-values()**関数では、整数値を xs:decimal にマップします。  
  
-   **Distinct-values()**関数のみをサポートします。 上記の型は基本型の組み合わせをサポートしていません。  
  
-   **Distinct-values()** xs:duration 型の値に対して関数がサポートされていません。  
  
-   照合順序を指定する構文オプションはサポートされません。  
  
## <a name="see-also"></a>参照  
 [xml データ型に対する XQuery 関数](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
