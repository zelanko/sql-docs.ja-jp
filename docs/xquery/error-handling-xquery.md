---
title: エラー処理 (XQuery) |Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- static errors
- errors [XQuery]
- XQuery, error handling
- dynamic errors [XQuery]
ms.assetid: 7dee3c11-aea0-4d10-9126-d54db19448f2
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 444fa51144535475f67cc0d073b63cb1b8354531
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47687290"
---
# <a name="error-handling-xquery"></a>エラー処理 (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  W3C の仕様では、型エラーが静的または動的に発生することを許可し、静的エラー、動的エラー、および型エラーを定義しています。  
  
## <a name="compilation-and-error-handling"></a>コンパイルとエラー処理  
 XQuery 式や XML DML ステートメントの構文が誤っている場合は、コンパイル エラーが返されます。 コンパイル フェーズでは、XQuery 式や DML ステートメントの静的な型が正しいことが確認され、XML スキーマを使用して型指定された XML にするための型の推定が行われます。 型の安全性違反により実行時に式が失敗する可能性がある場合は、静的な型エラーが発生します。 静的なエラーの例には、整数への文字列の追加、存在しないノードに対する型指定されたデータのクエリの実行などがあります。  
  
 W3C 標準からは外れますが、XQuery の実行時エラーは空のシーケンスに変換されます。 この空のシーケンスは、呼び出し時の状況に応じ、空の XML または NULL としてクエリの結果に反映される場合があります。  
  
 実行時のキャスト エラーは空のシーケンスに変換されますが、明示的に正しい型にキャストすることで静的なエラーを回避できます。  
  
## <a name="static-errors"></a>静的なエラー  
 使用して静的エラーが返されます、[!INCLUDE[tsql](../includes/tsql-md.md)]エラー メカニズムです。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]XQuery の型エラーが静的に返されます。 詳細については、次を参照してください。 [XQuery と静的な型指定](../xquery/xquery-and-static-typing.md)します。  
  
## <a name="dynamic-errors"></a>動的エラー  
 XQuery では、ほとんどの動的エラーが空のシーケンス ("()") にマップされます。 ただし、XQuery 集計関数でオーバーフローが発生する場合および XML-DML 検証エラーは例外です。 ほとんどの動的エラーは空のシーケンスにマップされることに注意してください。 動的エラーが空のシーケンスにマップされない場合、XML インデックスを利用するクエリの実行で予期しないエラーが発生する可能性があります。 そのため、[!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]では、予期しないエラーを発生させることなくクエリを効率的に実行するため、動的エラーが () にマップされます。  
  
 () は False にマップされています。そのため、多くの場合、述語内で動的エラーが発生する状況では、エラーが発生しないとセマンティクスは変更されません。 ただし、動的エラーではなく () を返すと予期しない結果が生じることがあります。 このことを示す例を次に挙げます。  
  
### <a name="example-using-the-avg-function-with-a-string"></a>例 : 文字列に対する avg() 関数の使用  
 次の例では、 [avg 関数](../xquery/aggregate-functions-avg.md)が呼び出され、3 つの値の平均を計算します。 これらの値の 1 つは文字列です。 この XML インスタンスは型指定されていないので、XML インスタンス内のすべてのデータは型指定されていないアトミック型になります。 **Avg()** 関数が最初にこれらの値をキャスト**xs:double**平均を計算する前にします。 ただし、値、`"Hello"`にキャストできない**xs:double**し、動的エラーを作成します。 動的エラーへのキャストを返すのではなく、この場合、`"Hello"`に**xs:double**により空のシーケンス。 **Avg()** 関数がこの値は無視、他の 2 つの値の平均を計算および 150 が返されます。  
  
```  
DECLARE @x xml  
SET @x=N'<root xmlns:myNS="test">  
 <a>100</a>  
 <b>200</b>  
 <c>Hello</c>  
</root>'  
SELECT @x.query('avg(//*)')  
```  
  
### <a name="example-using-the-not-function"></a>例 : not 関数の使用  
 使用すると、[機能しない](../xquery/functions-on-boolean-values-not-function.md)、述語内で`/SomeNode[not(Expression)]`式には、動的エラーが発生、空のシーケンスが返されますエラーではなく、します。 適用する**not()** 空のシーケンスには、エラーではなく True を返します。  
  
### <a name="example-casting-a-string"></a>例 : 文字列のキャスト  
 次の例では、リテラル文字列 "NaN" を xs:string にキャストしてから、xs:double にキャストします。 その結果、空の行セットが返されます。 文字列 "NaN" は xs:double に正しくキャストすることはできません。ただし、この文字列は最初に xs:string にキャストされているため、このことは実行時まで判断できません。  
  
```  
DECLARE @x XML  
SET @x = ''  
SELECT @x.query(' xs:double(xs:string("NaN")) ')  
GO  
```  
  
 次の例では静的な型エラーが発生します。  
  
```  
DECLARE @x XML  
SET @x = ''  
SELECT @x.query(' xs:double("NaN") ')  
GO  
```  
  
#### <a name="implementation-limitations"></a>実装の制限事項  
 **Fn:error()** 関数がサポートされていません。  
  
## <a name="see-also"></a>参照  
 [XQuery 言語リファレンス &#40;SQL Server&#41;](../xquery/xquery-language-reference-sql-server.md)   
 [XQuery の基礎](../xquery/xquery-basics.md)  
  
  
