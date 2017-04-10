---
title: "検索と置換 | Microsoft Docs"
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
  - "大文字と小文字の区別 [SQL Server]"
  - "元に戻す操作"
  - "検索 [SQL Server Management Studio]"
  - "テキストの置換"
  - "クイック検索と置換 [SQL Server Management Studio]"
  - "クエリ エディター [SQL Server Management Studio], 元に戻す"
  - "クエリ エディター [SQL Server Management Studio], 検索"
  - "正規表現 [SQL Server Management Studio]"
  - "テキストの検索 [SQL Server Management Studio]"
  - "テキスト [SQL Server], 検索と置換操作"
  - "検索 [SQL Server Management Studio]"
  - "テキストの特定"
  - "クエリ エディター [SQL Server Management Studio], テキストの置換"
  - "[検索と置換] ダイアログ ボックス"
  - "ワイルドカード オプション [SQL Server Management Studio]"
  - "単語単位 [SQL Server]"
  - "検索 [SQL Server Management Studio], 置換"
ms.assetid: 3641c7b3-3e3e-4ddd-af82-c15b50004f94
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 21
---
# 検索と置換
  テキストの検索と置換にはいくつかの方法があります。 **[編集]** メニューの **[検索と置換]** には、**[クイック検索]**、**[クイック置換]**、**[フォルダーを指定して検索]**、**[フォルダーを指定して置換]** という 4 つのオプションが用意されています。 各オプションを選択すると、各バージョンの **[検索と置換]** ダイアログ ボックスが表示されます。 ダイアログ ボックスを使用しないで、インクリメンタル検索キーボード ショートカット キーによって検索することも可能です。 これらの方法によって、検索と置換の範囲を設定することや、検索一致項目や置換項目を確認する方法を選択することができます。  
  
 テキストの検索と置換に関する注意点は次のとおりです。  
  
-   **[検索と置換]** ダイアログ ボックスで設定したオプションは、すべての検索操作に影響します。 具体的には、**[大文字と小文字を区別する]**、**[単語単位]**、**[上へ検索]**、**[非表示のテキストを検索]**、**[ワイルドカード]**、**[正規表現]**、**[検索対象: すべての開かれているドキュメント]**、**[検索対象: 現在のプロジェクト]** の各オプションです。 すべてのバージョンの **[検索と置換]** ダイアログ ボックスですべてのオプションを使用できるわけではありません。  
  
-   **[元に戻す]** を使用できるのは、置換操作後に開いたままにしておいたドキュメントに限られます。  
  
-   複数のファイルを対象にした **[すべて置換]** 操作に対して **[元に戻す]** を使用すると、すべての対象ファイルに対して一括処理が行われます。 つまり、一部のファイルの変更を元に戻し、他のファイルの変更をそのまま残す、ということはできません。  
  
 一般に、グラフィカル ビューを持つ項目の検索はできません。  
  
## 参照  
 [アクティブ ドキュメントのインクリメンタル検索](../../relational-databases/scripting/search-an-active-document-incrementally.md)   
 [ドキュメントの対話形式の検索](../../relational-databases/scripting/search-documents-interactively.md)   
 [結果一覧を使用してドキュメントを検索する方法](../../relational-databases/scripting/search-documents-using-results-lists.md)   
 [ワイルドカードを使用したテキスト検索](../../relational-databases/scripting/search-text-with-wildcards.md)   
 [正規表現によるテキストの検索](../../relational-databases/scripting/search-text-with-regular-expressions.md)  
  
  