---
title: "アクティブ ドキュメントのインクリメンタル検索 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "検索 [SQL Server Management Studio], インクリメンタル"
  - "クエリ エディター [SQL Server Management Studio], インクリメンタル検索"
  - "インクリメンタル検索 [SQL Server Management Studio]"
ms.assetid: 490bb36c-dd43-4219-9e2a-ff27046b9395
caps.latest.revision: 24
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 24
---
# アクティブ ドキュメントのインクリメンタル検索
  テキストを入力して、1 つのドキュメント内またはウィンドウ内のインクリメンタル検索を実行できます。 検索操作では、ドキュメント内またはウィンドウ内のインクリメンタル検索の対象として入力した文字の最初の一致項目のセットが強調表示されます。 インクリメンタル検索では、ドキュメント内またはウィンドウ内のテキストのうち、非表示になっているテキストが検索対象から自動的に除外されます。  
  
 インクリメンタル検索の場合、**[大文字と小文字を区別する]** オプションに関しては、直前の検索の基準がそのまま使用されます。 たとえば、**[フォルダーを指定して検索]** ダイアログ ボックスを使用して複数のファイルの検索を実行したときに **[大文字と小文字を区別する]** をオンにしていれば、次回のインクリメンタル検索でも大文字と小文字が区別されます。  
  
### インクリメンタル検索を実行するには  
  
1.  検索するファイルまたはウィンドウを開きます。  
  
2.  **[編集]** メニューの **[詳細設定]** をポイントし、**[インクリメンタル検索]** をクリックします。  
  
     カーソルのアイコンが、検索方向を示す矢印の付いた双眼鏡に変わり、ステータス バーに [インクリメンタル検索] と表示されます。  
  
3.  テキスト文字列の入力を始めます。  
  
     入力しているテキストがステータス バーに表示され、そのテキストの最初の一致項目がエディターで強調表示されます。 入力を続けると、エディターでは次の一致項目に移動して、その項目が強調表示されます。 一致項目がない場合は、ステータス バーに以下のメッセージが表示されます。  
  
    ```  
    Incremental Search: <text> (not found)  
    ```  
  
 インクリメンタル検索は、ドキュメント内の現在の位置を起点として、上から下へ、左から右へと進んでいきます。 キーボード ショートカット キーを使用してインクリメンタル検索を実行することも可能です。  
  
> [!NOTE]  
>  キーボード ショートカット キーの完全な一覧については、「[SQL Server Management Studio のキーボード ショートカット](../../tools/sql-server-management-studio/sql-server-management-studio-keyboard-shortcuts.md)」を参照してください。  
  
## 参照  
 [検索と置換](../../relational-databases/scripting/search-and-replace.md)   
 [ドキュメントの対話形式の検索](../../relational-databases/scripting/search-documents-interactively.md)   
 [結果一覧を使用してドキュメントを検索する方法](../../relational-databases/scripting/search-documents-using-results-lists.md)   
 [ワイルドカードを使用したテキスト検索](../../relational-databases/scripting/search-text-with-wildcards.md)   
 [正規表現によるテキストの検索](../../relational-databases/scripting/search-text-with-regular-expressions.md)  
  
  