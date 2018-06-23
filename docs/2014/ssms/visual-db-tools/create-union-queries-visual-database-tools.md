---
title: UNION クエリの作成 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- queries [SQL Server], types
- UNION queries
- Select query
- combining query results
- merged SELECT query [SQL Server]
ms.assetid: b5aafb1d-e4ed-4922-b790-56abc5ec551a
caps.latest.revision: 12
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fbfe0de4422aba4a73a5cabf16c42566c272a7d8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36164216"
---
# <a name="create-union-queries-visual-database-tools"></a>UNION クエリの作成 (Visual Database Tools)
  UNION キーワードを使用すると、2 つの SELECT ステートメントの結果を、1 つのテーブルに表示できます。 いずれかの SELECT ステートメントから返された行がすべて組み合わされて、UNION 式の結果として表示されます。 例については、次を参照してください。[選択例&#40;TRANSACT-SQL&#41;](/sql/t-sql/queries/select-examples-transact-sql)です。  
  
> [!NOTE]  
>  ダイアグラム ペインに表示できるのは、1 つの SELECT 句だけです。 したがって、UNION クエリを使用している場合、クエリ デザイナーにはテーブル操作ペインは表示されません。  
  
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
 [クエリの種類がサポートされている&#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [クエリおよびビューの操作方法に関するトピックをデザイン&#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md)   
 [クエリで基本的な操作を実行&#40;Visual Database Tools&#41;](perform-basic-operations-with-queries-visual-database-tools.md)   
 [共用体&#40;TRANSACT-SQL&#41;](/sql/t-sql/language-elements/set-operators-union-transact-sql)  
  
  
