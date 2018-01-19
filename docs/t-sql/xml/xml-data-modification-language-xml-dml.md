---
title: "XML データ変更言語 (XML DML) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|xml
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- modifying data [SQL Server], XML DML
- XML [SQL Server], DML
- XML DML [SQL Server]
- data modification language [XML DML]
- data modifications [XML DML]
- DML [XML in SQL Server]
- XQuery, XML DML
- xml data type [SQL Server], XML DML
ms.assetid: 20ce50d2-c07b-4e41-93a7-1380d2cd49cb
caps.latest.revision: "29"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 5b3315bad83aff77c661edb9e0b3e9e081147d42
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="xml-data-modification-language-xml-dml"></a>XML DML (XML データ変更言語)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  XML DML (XML データ変更言語) は、XQuery 言語の拡張言語です。 W3C で定義されているように、XQuery 言語には、データ操作の部分がありません。 このトピックでは、XQuery 言語で導入された XML DML は、完全に機能のクエリおよびデータ変更言語に対して使用することができますが、 **xml**データ型。  
  
 XML DML では、XQuery に次のキーワードが追加されました。これらのキーワードでは、大文字と小文字が区別されます。  
  
-   **insert**  
  
-   **delete**  
  
-   **値を置き換える**  
  
 」の説明に従って[XML データ型と列 &#40;です。SQL Server &#41;](../../relational-databases/xml/xml-data-type-and-columns-sql-server.md)の変数および列を作成することができます、 **xml**を入力し、それらに XML ドキュメントやフラグメントを割り当てます。 このような XML インスタンスを変更または更新するには、次の操作を実行します。  
  
-   使用して、 [modify() メソッドの xml データ型)](../../t-sql/xml/modify-method-xml-data-type.md)の**xml**データ型。  
  
-   内の適切な XML DML ステートメントの指定、 **modify()**メソッドです。  
  
 一部の属性では、挿入や削除、値の変更ができないので注意してください。 例:  
  
-   型指定の有無**xml、**属性は、 **xmlns**、 **xmlns:\***、および**xml:base**です。  
  
-   型指定された**xml**属性は、のみ、 **xsi:nil**、および**xsi:type**です。  
  
 その他の制限には、次のようなものがあります。  
  
-   型指定の有無**xml**、属性を挿入する**xml:base**は失敗します。  
  
-   型指定された**xml**、削除して、変更、 **xsi:nil**属性は失敗します。 型指定されていない**xml**属性を削除するか、その値を変更することができます。  
  
-   型指定された**xml**の値を変更する、 **xs:type**属性は失敗します。 型指定されていない**xml**属性の値を変更することができます。  
  
 型指定された xml インスタンスを変更する場合、最終的な形式が、その型の有効なインスタンスである必要があります。 そうでない場合は、検証エラーが返されます。  
  
## <a name="see-also"></a>参照  
 [insert &#40;です。XML DML&#41;](../../t-sql/xml/insert-xml-dml.md)   
 [delete &#40;です。XML DML&#41;](../../t-sql/xml/delete-xml-dml.md)   
 [置換値 &#40;です。XML DML&#41;](../../t-sql/xml/replace-value-of-xml-dml.md)   
 [型指定された XML と型指定されていない XML の比較](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [XML データのインスタンスの作成](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [xml データ型メソッド](../../t-sql/xml/xml-data-type-methods.md)  
  
  
