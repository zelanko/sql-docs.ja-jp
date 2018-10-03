---
title: XML 列でのビューの作成 | Microsoft Docs
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- views [XML in SQL Server]
ms.assetid: eb5f0439-1f69-49c2-8759-e59bda1633b7
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5e78c2bc024395d90a33d38c1edeba79c3635448
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47783336"
---
# <a name="create-views-over-xml-columns"></a>XML 列でのビューの作成
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  **xml** 型の列を使用して、ビューを作成することもできます。 次の例では、 `xml` xml **データ型の** value() **メソッドを使用して** 型の列の値を取得するビューを作成します。  
  
```  
-- Create the table.  
CREATE TABLE T (  
    ProductID          int primary key,   
    CatalogDescription xml)  
GO  
-- Insert sample data.  
INSERT INTO T values(1,'<ProductDescription ProductID="1" ProductName="SomeName" />')  
GO  
-- Create view (note the value() method used to retrieve ProductName   
-- attribute value from the XML).  
CREATE VIEW MyView AS   
  SELECT ProductID,  
         CatalogDescription.value('(/ProductDescription/@ProductName)[1]', 'varchar(40)') AS PName  
  FROM T  
GO   
```  
  
 このビューに対し、次のクエリを実行します。  
  
```  
SELECT *   
FROM   MyView  
```  
  
 結果を次に示します。  
  
```  
ProductID   PName        
----------- ------------  
1           SomeName   
```  
  
 **xml** データ型を使用してビューを作成する際には次の点に注意してください。  
  
-   xml データ型は、具体化されたビュー内に作成できます。 具体化されたビューは、xml データ型のメソッドに基づくことはできません。 ただし、ベース テーブルの xml 型の列とは異なる XML スキーマ コレクションにキャストできます。  
  
-   分散パーティション ビューには **xml** データ型を使用できません。  
  
-   ビューに対して実行される SQL 述語は、ビュー定義の XQuery には組み込まれません。  
  
-   ビューの XML データ型メソッドは更新できません。  
  
  
