---
title: XQuery 言語リファレンス (SQL サーバ) |マイクロソフトドキュメント
description: SQL Server の XQuery 言語について説明し、完全な言語リファレンスを参照してください。
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
helpviewer_keywords:
- XQuery
- XQuery, about XQuery
- xml data type [SQL Server], XQuery
- XML [SQL Server], XQuery
- queries [XML in SQL Server], XQuery
ms.assetid: 8a69344f-2990-4357-8160-cb26aac95b91
author: rothja
ms.author: jroth
ms.openlocfilehash: 35a1418e416e32ab5b8dc9647c4a9aa24700b624
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388612"
---
# <a name="xquery-language-reference-sql-server"></a>XQuery 言語リファレンス (SQL Server)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[tsql](../includes/tsql-md.md)]は **、xml**データ型のクエリに使用される XQuery 言語のサブセットをサポートします。 この XQuery 実装は、2004 年 7 月の XQuery の作業ドラフトと一致しています。 この言語は、すべての主要なデータベース ベンダーとマイクロソフトの参加により、ワールド ワイド Web コンソーシアム (W3C) によって開発中です。 W3C 仕様は、W3C 勧告になる前に将来の改訂を受ける可能性があるため、この実装は最終的な推奨事項とは異なる場合があります。 このトピックでは、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] でサポートされる XQuery サブセットのセマンティクスと構文について概説します。  
  
 詳細については[、W3C XQuery 1.0 言語仕様](https://go.microsoft.com/fwlink/?LinkId=48846)を参照してください。  
  
 XQuery は、構造化された XML データまたは半構造化 XML データを照会できる言語です。 で提供される**xml**データ型の[!INCLUDE[ssDE](../includes/ssde-md.md)]サポートを使用すると、ドキュメントをデータベースに格納し、XQuery を使用してクエリを実行できます。  
  
 XQuery は既存の XPath クエリ言語に基づいており、より優れた反復処理、より良い並べ替え結果、および必要な XML を構築する機能をサポートします。 XQuery は XQuery データ モデルで動作します。 これは XML ドキュメントの抽象化であり、型指定または型指定されていない XQuery の結果です。 型情報は W3C XML Schema 言語によって提供される型に基づきます。 入力情報がない場合、XQuery はデータを型なしとして処理します。 これは、XPath バージョン 1.0 が XML を処理する方法に似ています。  
  
 xml 型の変数または列に格納されている**XML**インスタンスを照会するには、 [xml データ型メソッド を](../t-sql/xml/xml-data-type-methods.md)使用します。 たとえば **、xml**型の変数を宣言し **、xml**データ型の**query()** メソッドを使用してクエリを実行できます。  
  
```sql
DECLARE @x xml  
SET @x = '<ROOT><a>111</a></ROOT>'  
SELECT @x.query('/ROOT/a')  
```  
  
 次の例では、AdventureWorks データベースの ProductModel テーブルの**xml**型の [命令] 列に対してクエリを指定します。  
  
```sql
SELECT Instructions.query('declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";           
    /AWMI:root/AWMI:Location[@LocationID=10]  
') as Result   
FROM  Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 XQuery には、名前空間の宣言`declare namespace``AWMI=...`、およびクエリ式が`/AWMI:root/AWMI:Location[@LocationID=10]`含まれています。  
  
 **XQuery は、xml**型の命令列に対して指定されることに注意してください。 xml データ型の[query() メソッド](../t-sql/xml/query-method-xml-data-type.md)を使用して、XQuery を指定します。  
  
 次の表は、[!INCLUDE[ssDE](../includes/ssde-md.md)]での XQuery の実装を理解する際に役立つ関連トピックを示しています。  
  
|トピック|説明|  
|-----------|-----------------|  
|[XML データ &#40;SQL Server&#41;](../relational-databases/xml/xml-data-sql-server.md)|の**xml**データ型[!INCLUDE[ssDE](../includes/ssde-md.md)]と、このデータ型に対して使用できるメソッドのサポートについて説明します。 **xml**データ型は、XQuery 式が実行される入力 XQuery データ モデルを形成します。|  
|[XML スキーマ コレクション &#40;SQL Server&#41;](../relational-databases/xml/xml-schema-collections-sql-server.md)|データベースに格納されている XML インスタンスを型指定する方法について説明します。 つまり、XML スキーマ コレクションを**XML**型の列に関連付けることができます。 列に格納されているすべてのインスタンスは、コレクション内のスキーマに対して検証および型指定され、XQuery の型情報を提供します。|  
|||  
  
> [!NOTE]  
>  このセクションの構成は、W3C (World Wide Web Consortium) XQuery ワーキング ドラフト仕様に基づいています。 このセクションで提供する図の一部は、その仕様から引用したものです。 このセクションでは、Microsoft XQuery の実装と W3C 仕様を比較し、マイクロソフトの XQuery が W3C とどのように異なるかを説明し、W3C の機能がサポートされていないものを示します。 W3C 仕様は で[http://www.w3.org/TR/2004/WD-xquery-20040723](https://go.microsoft.com/fwlink/?LinkId=48846)入手できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|説明|  
|-----------|-----------------|  
|[XQuery の基礎](../xquery/xquery-basics.md)|XQuery の概念の基本的な概要、および式の評価 (静的および動的コンテキスト)、アトマイゼーション、有効なブール値、XQuery 型システム、シーケンス型の一致、およびエラー処理について説明します。|  
|[XQuery 式](../xquery/xquery-expressions.md)|XQuery 原始式、パス式、シーケンス式、算術式、比較式、論理式、XQuery の構築、FLWOR 式、条件式、量化式、およびシーケンス型のさまざまな式について説明します。|  
|[モジュールとプロローグ&#40;XQuery&#41;](../xquery/modules-and-prologs-xquery.md)|XQuery プロローグについて説明します。|  
|[xml データ型に対する XQuery 関数](../xquery/xquery-functions-against-the-xml-data-type.md)|サポートされている XQuery 関数の一覧について説明します。|  
|[xml データ型に対する XQuery の演算子](../xquery/xquery-operators-against-the-xml-data-type.md)|サポートされている XQuery 演算子について説明します。|  
|[xml データ型に対する XQuery のその他のサンプル](../xquery/additional-sample-xqueries-against-the-xml-data-type.md)|XQuery の追加サンプルを提供します。|  
  
## <a name="see-also"></a>参照  
 [XML データ &#40;SQL Server&#41;](../relational-databases/xml/xml-data-sql-server.md)   
 [XML スキーマ コレクション&#40;SQL Server&#41;](../relational-databases/xml/xml-schema-collections-sql-server.md)   
 [XML ドキュメントの一括インポートと一括エクスポートの例 &#40;SQL Server&#41;](../relational-databases/import-export/examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
  
  
