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
ms.topic: article
helpviewer_keywords:
- views [XML in SQL Server]
ms.assetid: eb5f0439-1f69-49c2-8759-e59bda1633b7
caps.latest.revision: 14
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: ec628981acc51d660a0e8a99dba991d957955e9b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36175114"
---
# <a name="create-views-over-xml-columns"></a>XML 列でのビューの作成
  使用することができます、`xml`ビューを作成する型の列です。 次の例では、ビューを作成する値を`xml`を使用して型の列を取得、`value()`のメソッド、`xml`データ型。  
  
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
  
-   `xml`分散パーティション ビューにデータ型を使用することはできません。  
  
-   ビューに対して実行される SQL 述語は、ビュー定義の XQuery には組み込まれません。  
  
-   ビューの XML データ型メソッドは更新できません。  
  
  