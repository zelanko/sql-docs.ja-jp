---
title: "Transact-SQL スニペットの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IntelliSense [SQL Server], スニペットの作成"
  - "スニペット [Transact-SQL], 作成"
  - "Transact-SQL スニペット, 作成"
ms.assetid: a8316a58-bb57-485e-845f-84c23360314c
caps.latest.revision: 6
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 6
---
# Transact-SQL スニペットの作成
  [!INCLUDE[tsql](../../includes/tsql-md.md)] コード スニペットがスクリプトに挿入されると、スニペットのコンテンツを編集して [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを作成できます。  
  
## スニペットの作成  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] スニペットをスクリプトに追加した場合、挿入されたスニペット ステートメントには 1 つ以上の置換ポイントが含まれ、強調表示されます。 置換ポイント上にマウス ポインターを置くと、指定できる構文要素の説明を含むツールヒントが表示されます。 [!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディターは、ソース ファイルを閉じるまで、スニペットを周囲のスクリプトと区別します。 ソース ファイルを閉じるまで、置換ポイントはアクティブのままになります。  
  
 スニペットによって挿入されたテンプレート コードに追加の構文要素も追加できます。 たとえば、テーブルの作成スニペット テンプレートは、2 列の定義を生成します。3 列以上のテーブルを作成するには、列定義を追加する必要があります。  
  
#### スニペット ステートメントの作成  
  
1.  1 つの置換ポイントから次の置換ポイントに移動するには、Tab キーを使用します。 前の置換ポイントに移動するには、Shift キーを押しながら Tab キーを押します。  
  
2.  IntelliSense を呼び出すには、Ctrl キーを押しながら Space キーを押します。  
  
3.  一覧からアイテムを選択するか、置換を入力します。  
  
## 参照  
 [Transact-SQL スニペットの挿入](../../relational-databases/scripting/insert-transact-sql-snippets.md)   
 [ブロックの挿入 Transact-SQL スニペットの挿入](../../relational-databases/scripting/insert-surround-with-transact-sql-snippets.md)  
  
  