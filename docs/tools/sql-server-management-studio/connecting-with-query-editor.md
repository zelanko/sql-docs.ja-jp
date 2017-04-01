---
title: "クエリ エディターとの接続 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 48725f54-a7b6-4b79-948e-965c1fe4eef1
caps.latest.revision: 26
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# クエリ エディターとの接続
[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] では、サーバーから切断されていてもコードの記述と編集を行うことができます。 この機能は、サーバーを利用できない場合、またはサーバーやネットワークの限られたリソースを節約したい場合に有効です。 さらに、新しいクエリ エディター ウィンドウを開いたり、コードを再入力したりしなくても、クエリ エディターの接続を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の新しいインスタンスに変更することもできます。  
  
## オフラインでのコーディング  
  
#### コードをオフラインで記述した後、別のサーバーに接続するには  
  
1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] のツール バーの **[データベース エンジン クエリ]** をクリックして、クエリ エディターを開きます。  
  
2.  **[データベース エンジンへの接続]** ダイアログ ボックスで、**[キャンセル]** をクリックします。 クエリ エディターを開きます。クエリ エディターのタイトル バーから、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続されていないことがわかります。  
  
3.  コード ペインに次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを入力します。  
  
    ```  
    SELECT * FROM Production.Product;  
    GO  
    ```  
  
    この時点で、**[接続]**、**[実行]**、**[解析]**、または **[推定実行プランの表示]** をクリックすることにより、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続できます。これらのオプションは、**[クエリ]** メニュー、クエリ エディターのツール バー、または [クエリ エディター] ウィンドウを右クリックすると表示されるショートカット メニューから実行できます。 この実習ではツール バーを使用します。  
  
4.  ツール バーの **[実行]** ボタンをクリックします。**[データベース エンジンへの接続]** ダイアログ ボックスが表示されます。  
  
5.  **[サーバー名]** ボックスにサーバー名を入力し、**[オプション]** をクリックします。  
  
6.  **[接続プロパティ]** タブで、**[データベースへの接続]** ボックスの一覧から [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] を選択し、**[接続]** をクリックします。  
  
7.  同じサーバーに接続する別のクエリ エディター ウィンドウを開くには、ツール バーの **[新しいクエリ]** をクリックします。  
  
8.  接続先を変更するには、クエリ エディター ウィンドウを右クリックし、**[接続]** をポイントして、**[接続の変更]** をクリックします。  
  
9. **[サーバーへの接続]** ダイアログ ボックスで、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の別の有効なインスタンスを選択し、**[接続]** をクリックします。  
  
クエリ エディターの新機能により、複数のサーバーで同じコードを容易に実行できます。 類似する複数のサーバーの保守を行う場合などは、この機能を使用すると便利です。  
  
## このレッスンの次の作業  
[インデントの追加](../../tools/sql-server-management-studio/adding-indentation.md)  
  
  
  
