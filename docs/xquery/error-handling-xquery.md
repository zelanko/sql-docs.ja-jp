---
title: エラー処理 (XQuery) |Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
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
ms.openlocfilehash: 1be899b95a4e132c3b5aa42a73df9bd1b0ee057c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68038965"
---
# <a name="error-handling-xquery"></a>エラー処理 (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  W3C 仕様では、型エラーが静的または動的に発生し、静的なエラー、動的エラー、および型エラーが定義されています。  
  
## <a name="compilation-and-error-handling"></a>コンパイルとエラー処理  
 XQuery 式や XML DML ステートメントの構文が誤っている場合は、コンパイル エラーが返されます。 コンパイルフェーズでは、XQuery 式および DML ステートメントの静的な型の正確性を確認し、型指定された XML の型推論に XML スキーマを使用します。 型の安全性違反により実行時に式が失敗する可能性がある場合は、静的な型エラーが発生します。 静的なエラーの例には、整数への文字列の追加、存在しないノードに対する型指定されたデータのクエリの実行などがあります。  
  
 W3C 標準からの逸脱として、XQuery の実行時エラーは空のシーケンスに変換されます。 この空のシーケンスは、呼び出し時の状況に応じ、空の XML または NULL としてクエリの結果に反映される場合があります。  
  
 正しい型に明示的にキャストすると、ユーザーは静的エラーを回避できます。ただし、実行時のキャストエラーは空のシーケンスに変換されます。  
  
## <a name="static-errors"></a>静的エラー  
 エラーメカニズムを使用して、 [!INCLUDE[tsql](../includes/tsql-md.md)]静的エラーが返されます。 で[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]は、XQuery 型エラーが静的に返されます。 詳細については、「 [XQuery と静的](../xquery/xquery-and-static-typing.md)な型指定」を参照してください。  
  
## <a name="dynamic-errors"></a>動的エラー  
 XQuery では、ほとんどの動的エラーが空のシーケンス ("()") にマップされます。 ただし、これらの例外は、XQuery アグリゲーター関数のオーバーフロー状態と XML DML 検証エラーの2つです。 ほとんどの動的エラーは空のシーケンスにマップされることに注意してください。 そうしないと、XML インデックスを利用してクエリを実行すると、予期しないエラーが発生することがあります。 そのため、[!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]では、予期しないエラーを発生させることなくクエリを効率的に実行するため、動的エラーが () にマップされます。  
  
 多くの場合、述語内で動的エラーが発生する状況では、() が False にマップされているため、エラーを発生させてもセマンティクスが変更されることはありません。 ただし、動的エラーではなく () を返すと予期しない結果が生じることがあります。 これを説明する例を次に示します。  
  
### <a name="example-using-the-avg-function-with-a-string"></a>例: 文字列で avg () 関数を使用する  
 次の例では、 [avg 関数](../xquery/aggregate-functions-avg.md)を呼び出して、3つの値の平均を計算します。 これらの値の1つは文字列です。 この場合、XML インスタンスは型指定されていないため、その中のすべてのデータは型指定されていないアトミック型になります。 **Avg ()** 関数は、平均値を計算する前に、最初にこれらの値を**xs: double**にキャストします。 ただし、値を`"Hello"` **xs: double**にキャストして、動的エラーを作成することはできません。 この場合、を`"Hello"` **xs: double**にキャストすると、空のシーケンスが返されます。 **Avg ()** 関数は、この値を無視し、他の2つの値の平均を計算し、150を返します。  
  
```  
DECLARE @x xml  
SET @x=N'<root xmlns:myNS="test">  
 <a>100</a>  
 <b>200</b>  
 <c>Hello</c>  
</root>'  
SELECT @x.query('avg(//*)')  
```  
  
### <a name="example-using-the-not-function"></a>例: not 関数の使用  
 たとえば、 `/SomeNode[not(Expression)]`、などの述語で[not 関数](../xquery/functions-on-boolean-values-not-function.md)を使用した場合、式によって動的エラーが発生すると、エラーではなく空のシーケンスが返されます。 空のシーケンスに**not ()** を適用すると、エラーではなく True が返されます。  
  
### <a name="example-casting-a-string"></a>例: 文字列のキャスト  
 次の例では、リテラル文字列 "NaN" が xs: string にキャストされ、次に xs: double にキャストされます。 その結果、空の行セットが返されます。 文字列 "NaN" は xs:double に正しくキャストすることはできません。ただし、この文字列は最初に xs:string にキャストされているため、このことは実行時まで判断できません。  
  
```  
DECLARE @x XML  
SET @x = ''  
SELECT @x.query(' xs:double(xs:string("NaN")) ')  
GO  
```  
  
 ただし、この例では、静的な型のエラーが発生します。  
  
```  
DECLARE @x XML  
SET @x = ''  
SELECT @x.query(' xs:double("NaN") ')  
GO  
```  
  
#### <a name="implementation-limitations"></a>実装の制限事項  
 **Fn: error ()** 関数はサポートされていません。  
  
## <a name="see-also"></a>参照  
 [XQuery 言語リファレンス &#40;SQL Server&#41;](../xquery/xquery-language-reference-sql-server.md)   
 [XQuery の基礎](../xquery/xquery-basics.md)  
  
  
