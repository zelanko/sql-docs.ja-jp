---
title: XML 列でのビューの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- views [XML in SQL Server]
ms.assetid: eb5f0439-1f69-49c2-8759-e59bda1633b7
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3f575b1a21efa30d2317cff644b65c73150c4ac1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37170183"
---
# <a name="create-views-over-xml-columns"></a>XML 列でのビューの作成
  使用することができます、`xml`ビューを作成する型の列。 次の例では、ビューを作成する値を`xml`を使用して型の列を取得、`value()`のメソッド、`xml`データ型。  
  
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
  
 使用して、次の点に注意してください、`xml`ビューを作成するデータ型。  
  
-   xml データ型は、具体化されたビュー内に作成できます。 具体化されたビューは、xml データ型のメソッドに基づくことはできません。 ただし、ベース テーブルの xml 型の列とは異なる XML スキーマ コレクションにキャストできます。  
  
-   `xml`分散パーティション ビューでデータ型は使用できません。  
  
-   ビューに対して実行される SQL 述語は、ビュー定義の XQuery には組み込まれません。  
  
-   ビューの XML データ型メソッドは更新できません。  
  
  
