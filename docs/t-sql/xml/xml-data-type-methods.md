---
title: "xml データ型のメソッド |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|xml
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- xml data type [SQL Server], methods
- methods [XML in SQL Server]
ms.assetid: d112b9c9-be9f-435c-a9e6-d21b65778fb7
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 3a08e2e0c49c707150df9f350cb9060203fd6f62
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="xml-data-type-methods"></a>xml データ型のメソッド
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  使用することができます、 **xml**データ型の変数またはの列に格納されている XML インスタンスのクエリを実行するメソッド**xml**型です。 このセクションのトピックを使用する方法について説明、 **xml**データ型のメソッドです。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|Description|  
|-----------|-----------------|  
|[クエリ &#40; #41メソッド &#40;xml データ型&#41;](../../t-sql/xml/query-method-xml-data-type.md)|query() メソッドを使用して XML インスタンスに対してクエリを実行する方法について説明します。|  
|[値 &#40; &#41;メソッド &#40;xml データ型&#41;](../../t-sql/xml/value-method-xml-data-type.md)|value() メソッドを使用して XML インスタンスから SQL 型の値を取得する方法について説明します。|  
|[存在 (& m); #40&#41;メソッド &#40;xml データ型&#41;](../../t-sql/xml/exist-method-xml-data-type.md)|exist() メソッドを使用して、クエリから空でない結果が返されるかどうかを判断する方法について説明します。|  
|[変更 (& m); #40&#41;メソッド &#40;xml データ型&#41;](../../t-sql/xml/modify-method-xml-data-type.md)|Modify() メソッドを使用して指定する方法について説明[XML データ変更言語 &#40;です。XML DML&#41;](../../t-sql/xml/xml-data-modification-language-xml-dml.md)更新を実行するステートメント。|  
|[ノード &#40; #41メソッド &#40;xml データ型&#41;](../../t-sql/xml/nodes-method-xml-data-type.md)|nodes() メソッドを使用して、XML を複数行に細分化し、XML ドキュメントの各部分をそれぞれ行セットに反映する方法について説明します。|  
|[XML データ内部のリレーショナル データのバインド](../../t-sql/xml/binding-relational-data-inside-xml-data.md)|XML 内部の XML 以外のデータをバインドする方法について説明します。|  
|[xml データ型メソッドの使用に関するガイドライン](../../t-sql/xml/guidelines-for-using-xml-data-type-methods.md)|使用するためのガイドラインについて説明します、 **xml**データ型のメソッドです。|  
  
 これらのメソッドは、ユーザー定義型メソッドの呼び出し構文を使用して呼び出します。 例:  
  
```  
SELECT XmlCol.query(' ... ')  
FROM   Table  
```  
  
> [!NOTE]  
>  **Xml**データ型のメソッド**query()**、 **value()**、および**exist()** NULL の XML インスタンスに対して実行された場合に NULL を返します。 また、 **modify()** 、何も返しませんが、 **nodes()**入力が null の行セットと空の行セットを返します。  
  
## <a name="see-also"></a>参照  
 [型指定された XML と型指定されていない XML の比較](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [XML データのインスタンスの作成](../../relational-databases/xml/create-instances-of-xml-data.md)  
  
  
