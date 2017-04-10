---
title: "SQL Server ドキュメントのオフライン アクセス | Microsoft Docs"
ms.custom: ""
ms.date: "08/22/2016"
ms.prod: "sql-non-specified"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "server-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 257ed357-8cbb-43bd-b042-254be5fbb977
caps.latest.revision: 6
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 6
---
# SQL Server ドキュメントのオフライン アクセス

SQL Server 2016 技術ドキュメントをオフラインで表示します。
  
## 前提条件
SQL Server 2016 の技術ドキュメントをオフラインで表示するには、下記と共にインストールされる HelpViewer 2.2 が必要です。 
- [Visual Studio 2015 (Community を含む任意のエディション)](https://www.visualstudio.com/products/visual-studio-community-vs.aspx) または
- [SQL Server Management Studio (SSMS) 2016 年 4 月の Preview (13.0.12500.29) 以降](https://msdn.microsoft.com/library/mt238290.aspx)

次の手順に進む前に、これらのいずれかをインストールします。
  
## SQL Server のオフライン技術ドキュメントのインストール 

1. Visual Studio 2015 の任意のバージョンまたは SSMS 2016 年 4 月の Preview ビルド以降をインストールします。 
2. SSMS または Visual Studio を起動します。
3. 上部のナビゲーション バーにある **[ヘルプ]** メニューで、**[ヘルプ コンテンツの追加と削除]** を選択します。 

#### (この操作を行うと、HelpViewer が起動します)

4. HelpViewer で、既定の [インストール元:] の **[オンライン]** を選択します。 
5. インストールするすべてのドキュメントの横の **[追加]** をクリックします。
6. 画面の右下にある **[更新]** ボタンをクリックして、選択したドキュメントをダウンロードおよびインストールします。
![オフライン コンテンツの読み込み](../sql-server/media/load-offline-content.png) 

 >** 重要!!** [更新] をクリックすると、HelpViewer はフリーズやハングすることになります。 まだ、選択したドキュメントをダウンロードおよびインストールしています。 **この問題を解決するには**、タスク マネージャーで HelpViewer を終了し、上記の手順 3 に従ってコンピューターを再起動します。 初めて HelpViewer がフリーズやハングした場合は、[次の手順](https://msdn.microsoft.com/library/mt654096.aspx)も実行してください。 これらの手順は一度だけ実行する必要がありますが、コンテンツを更新する度に、タスク マネージャーで HelpViewer を終了する必要がある場合があります。  
6. [ヘルプ] の [コンテンツの追加と削除] をもう一度選択して、HelpViewer を再起動します。 これで、オフライン ドキュメントを使用する準備ができました。



   ![オフラインの使用準備完了](../sql-server/media/offline-ready-to-use.png)


