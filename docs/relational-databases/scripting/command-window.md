---
title: "[コマンド] ウィンドウ | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.CommandWindow"
helpviewer_keywords: 
  - "[コマンド] ウィンドウ [Transact-SQL]"
ms.assetid: e567ebf9-0793-451b-92c7-26193a02d9da
caps.latest.revision: 14
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# [コマンド] ウィンドウ
  **[コマンド]** ウィンドウを使用すると、現在デバッグ中の[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] クエリ エディター ウィンドウのコードに対してデバッグ コマンドや編集コマンドなどのコマンドを実行できます。 **[コマンド]** ウィンドウを使用するには、デバッグ モードである必要があります。 [!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] の **[コマンド]** ウィンドウでもサポートされているコマンドの多くをサポートしています。 詳細については、[Visual Studio のコマンド ウィンドウに関するページ](http://go.microsoft.com/fwlink/?LinkId=112007)を参照してください。  
  
## タスク一覧  
 **[コマンド] ウィンドウにアクセスするには**  
  
-   **[デバッグ]** メニューの **[デバッグの開始]**をクリックします。  
  
 **変数の値を出力するには**  
  
-   **[コマンド]** ウィンドウで、「**Debug.Print \<変数名>**」と入力し、Enter キーを押します。  
  
 **現在のスレッドに関する情報を一覧表示するには**  
  
-   **[コマンド]** ウィンドウで、「**Debug.ListThread**」と入力し、Enter キーを押します。  
  
 **[クイック ウォッチ] ウィンドウに変数を追加するには**  
  
-   **[コマンド]** ウィンドウで、「**Debug.QuickWatch \<変数名>**」と入力し、Enter キーを押します。  
  
## 参照  
 [Transact-SQL デバッガー](../../relational-databases/scripting/transact-sql-debugger.md)  
  
  