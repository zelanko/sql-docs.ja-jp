---
title: "インデントの追加 | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: 9dce05c1-c52f-455d-8b8d-6f303e242760
caps.latest.revision: 25
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: HT
ms.sourcegitcommit: 5db067d5a2fe5bbf9953484c9a999ed7b1fcddae
ms.openlocfilehash: 55241a0b99024f557718654869d0ab728089e569
ms.contentlocale: ja-jp
ms.lasthandoff: 07/31/2017

---
# <a name="lesson-2-2---adding-indentation"></a>レッスン 2-2 - インデントの追加
クエリ エディターでは、大規模なコードのセクションに一括してインデントを適用できるほか、インデント幅を変更できます。  
  
## <a name="indenting-code"></a>コードへのインデントの適用  
  
#### <a name="to-indent-multiple-lines-of-code"></a>複数行のコードにインデントを適用するには  
  
1.  ツール バーの **[新しいクエリ]**をクリックします。  
  
2.  ここでは、 **Person**スキーマの **Person**テーブルから、 **BusinessEntityID** 、FirstName、 **MiddleName** 、 **LastName** の各列を選択する新しいクエリを作成します。 次のようにコードを入力します。各列を別々の行に入力してください。  
  
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
  
3.  `BusinessEntityID` から `LastName`までのテキストをすべて選択します。  
  
4.  **[SQL エディター]** ツール バーの **[インデント]** をクリックし、すべての行に一括してインデントを適用します。  
  
#### <a name="to-change-the-default-indentation"></a>既定のインデントを変更するには  
  
1.  **[ツール]** メニューの **[オプション]**をクリックします。  
  
2.  **[テキスト エディター]**、 **[すべての言語]**の順に展開し、 **[タブ]** をクリックして、適切なインデント幅を設定します。 インデント幅とタブのサイズを変更できるほか、タブをスペースに変換するかどうかも指定できます。  
  
    ![[タブ] ダイアログ ボックスの表示](./media/lesson-2-2-adding-indentation/tabsdialog.gif "[タブ] ダイアログ ボックスの表示")  
  
3.  **[OK]**をクリックします。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
[クエリ エディターの最大化](../../tools/sql-server-management-studio/lesson-2-3-maximizing-query-editor.md)  
  
  
  

