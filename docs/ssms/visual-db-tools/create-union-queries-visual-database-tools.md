---
title: "UNION クエリの作成 (Visual Database Tools) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- queries [SQL Server], types
- UNION queries
- Select query
- combining query results
- merged SELECT query [SQL Server]
ms.assetid: b5aafb1d-e4ed-4922-b790-56abc5ec551a
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 6c1ec545f2175067a3e4d6f9f625356607cb0eb4
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="create-union-queries-visual-database-tools"></a>UNION クエリの作成 (Visual Database Tools)
UNION キーワードを使用すると、2 つの SELECT ステートメントの結果を、1 つのテーブルに表示できます。 いずれかの SELECT ステートメントから返された行がすべて組み合わされて、UNION 式の結果として表示されます。 例については、「 [SELECT の例 (Transact-SQL)](http://msdn.microsoft.com/en-us/9b9caa3d-e7d0-42e1-b60b-a5572142186c)」を参照してください。  
  
> [!NOTE]  
> ダイアグラム ペインに表示できるのは、1 つの SELECT 句だけです。 したがって、UNION クエリを使用している場合、クエリ デザイナーにはテーブル操作ペインは表示されません。  
  
### <a name="to-create-a-merged-select-query"></a>マージされた選択クエリを作成するには  
  
1.  クエリを開くか、新規作成します。  
  
2.  SQL ペインに有効な UNION 式を入力します。  
  
    次の例は、有効な UNION 式です。  
  
    ```  
    SELECT ProductModelID, Name  
    FROM Production.ProductModel  
    UNION  
    SELECT ProductModelID, Name   
    FROM dbo.Gloves;  
    ```  
  
3.  **[クエリ デザイナー]** メニューの **[SQL の実行]** をクリックして、クエリを実行します。  
  
    UNION クエリがクエリ デザイナーによって書式化されます。  
  
## <a name="see-also"></a>参照  
[サポートされるクエリの種類 (Visual Database Tools)](../../ssms/visual-db-tools/supported-query-types-visual-database-tools.md)  
[クエリおよびビューのデザインの操作方法に関するトピック (Visual Database Tools)](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
[クエリに関する基本操作の実行 (Visual Database Tools)](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
[UNION (Transact-SQL)](http://msdn.microsoft.com/en-us/607c296f-8a6a-49bc-975a-b8d0c0914df7)  
  

