---
title: "算術式 (XQuery) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
dev_langs: XML
helpviewer_keywords:
- expressions [XQuery], arithmetic
- arithmetic expressions
ms.assetid: 90d675bf-56da-459a-9771-8cd13920a9fc
caps.latest.revision: "16"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0736594cec09f9deb31340ab4d4e3c1fa052496b
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="arithmetic-expressions-xquery"></a>算術式 (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  すべての算術演算子がサポートされている、除く**idiv**です。 次の例は、算術演算子の基本的な使用方法を示しています。  
  
```  
DECLARE @x xml  
SET @x=''  
SELECT @x.query('2 div 2')  
SELECT @x.query('2 * 2')  
```  
  
 **Idiv**が使用するソリューションは、サポートされていません、 **xs:integer()**コンス トラクター。  
  
```  
DECLARE @x xml  
SET @x=''  
-- Following will not work  
-- SELECT @x.query('2 idiv 2')  
-- Workaround   
SELECT @x.query('xs:integer(2 div 3)')  
```  
  
 算術演算子を使用した演算結果の型は入力値の型によって決まります。 オペランドどうしの型が異なる場合、必要に応じて一方または両方のオペランドが、データ型階層に基づき共通のプリミティブな基本データ型にキャストされます。 型の階層構造については、次を参照してください。[型キャストの規則では、XQuery](../xquery/type-casting-rules-in-xquery.md)です。  
  
 数値データ型の上位変換は、2 つのオペランドが異なる数値基本データ型である場合に行われます。 たとえば、追加する、 **xs:decimal**を**xs:double** double 型の値を 10 進数の値がまずします。 次に、結果が double 型の値となる加算処理が行われます。  
  
 型指定されていないアトミック値がもう一方のオペランドの数値基本型、またはキャストされた**xs:double**もう一方のオペランドも型指定された場合。  
  
## <a name="implementation-limitations"></a>実装の制限事項  
 制限事項を次に示します。  
  
-   算術演算子の引数が数値型にする必要がありますまたは**untypedAtomic**です。  
  
-   操作**xs:integer**値型の値で結果**xs:decimal**の代わりに**xs:integer**です。  
  
  
