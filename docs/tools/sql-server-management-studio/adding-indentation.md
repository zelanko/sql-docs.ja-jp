---
title: "インデントの追加 | Microsoft Docs"
ms.custom: ""
ms.date: "02/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 9dce05c1-c52f-455d-8b8d-6f303e242760
caps.latest.revision: 25
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# インデントの追加
クエリ エディターでは、大規模なコードのセクションに一括してインデントを適用できるほか、インデント幅を変更できます。  
  
## コードへのインデントの適用  
  
#### 複数行のコードにインデントを適用するには  
  
1.  ツール バーの **[新しいクエリ]**をクリックします。  
  
2.  ここでは、**Person** スキーマの **Person** テーブルから、**BusinessEntityID**、FirstName、**MiddleName**、**LastName** の各列を選択する新しいクエリを作成します。 次のようにコードを入力します。各列を別々の行に入力してください。  
  
    ```  
    -- Search for a contact  
    SELECT   
    BusinessEntityID,  
    FirstName,   
    MiddleName,   
    LastName  
    FROM Person.Person  
    WHERE LastName = 'Sanchez';  
    GO  
    ```  
  
3.  `BusinessEntityID` から `LastName` までのテキストをすべて選択します。  
  
4.  **[SQL エディター]** ツール バーの **[インデント]** をクリックし、すべての行に一括してインデントを適用します。  
  
#### 既定のインデントを変更するには  
  
1.  **[ツール]** メニューの **[オプション]**をクリックします。  
  
2.  **[テキスト エディター]**、**[すべての言語]** の順に展開し、**[タブ]** をクリックして、適切なインデント幅を設定します。 インデント幅とタブのサイズを変更できるほか、タブをスペースに変換するかどうかも指定できます。  
  
    ![[タブ] オプション ([オプション] ダイアログ ボックス)](../../tools/sql-server-management-studio/media/tabsdialog.gif "[タブ] オプション ([オプション] ダイアログ ボックス)")  
  
3.  **[OK]**をクリックします。  
  
## このレッスンの次の作業  
[クエリ エディターの最大化](../../tools/sql-server-management-studio/maximizing-query-editor.md)  
  
  
  
