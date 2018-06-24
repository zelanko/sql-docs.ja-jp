---
title: '[サーバーへの接続] ([接続プロパティ] ページ) (データベース エンジン) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.connecttosqlserver.connectionproperties.f1
ms.assetid: edc1143c-6a47-4b02-92ab-441bdea8ea8a
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f79ba89862334e19c3e50b347588de4e4183afaa
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36072260"
---
# <a name="connect-to-server-connection-properties-page-database-engine"></a>[サーバーへの接続] \([接続プロパティ] ページ) (データベース エンジン)
  このタブを使用すると、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスに接続するとき、または [!INCLUDE[ssDE](../../includes/ssde-md.md)] を **登録済みサーバー**に登録するときのオプションを表示または指定できます。 **のインスタンスに接続するときには、** [接続] **および** [オプション] [!INCLUDE[ssDE](../../includes/ssde-md.md)]のみがこのダイアログ ボックスに表示されます。 **を登録するときには、** [テスト] **および** [保存] [!INCLUDE[ssDE](../../includes/ssde-md.md)]のみがこのダイアログ ボックスに表示されます。  
  
## <a name="options"></a>および  
 **[データベースへの接続]**  
 接続するデータベースを一覧から選択します。 選択した場合**\<既定 >** サーバーの既定のデータベースに接続されます。 選択した場合**\<参照サーバー >**、接続先データベースのサーバーを参照することができます。  
  
 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] を通じて [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース エンジンのインスタンスに接続する場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用し、**[サーバーへの接続]** ダイアログ ボックスの **[接続プロパティ]** タブでデータベースを指定する必要があります。**[暗号化接続]** チェック ボックスがオンになっていることを確認してください。  
  
 既定では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は **master**に接続されます。 ユーザー データベースを指定すると、オブジェクト エクスプローラーにそのデータベースとそのオブジェクトのみが表示されます。 **master**に接続すると、すべてのデータベースを表示できるようになります。 詳しくは、「 [Windows Azure SQL Database Overview](http://go.microsoft.com/fwlink/?LinkId=163948)」(Microsoft Azure SQL Database の概要) をご覧ください。  
  
 **[ネットワーク プロトコル]**  
 一覧からプロトコルを選択します。 使用できるクライアント プロトコルは、[コンピューターの管理] の [SQL Native Client の構成] を使用して設定されたプロトコルです。  
  
 **[ネットワーク パケット サイズ]**  
 送信されるネットワーク パケットのサイズを入力します。 既定値は 4096 バイトです。  
  
 **[接続タイムアウト]**  
 接続の確立を待機するタイムアウトまでの秒数を入力します。既定値は 15 秒です。  
  
 **[実行タイムアウト]**  
 タスクの実行がサーバーで完了するまで待機する秒数を入力します。 既定値は 0 秒です。つまり、タイムアウトはありません。  
  
 **[暗号化接続]**  
 接続の暗号化を強制します。  
  
 **[作成した色を使用する]**  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のクエリ エディター ウィンドウのステータス バーの背景色を指定します。 色を指定するには、 **[選択]** をクリックします。 **[色の設定]** ダイアログ ボックスで、 **[基本色]** グリッドから定義済みの色を選択するか、 **[色の作成]** をクリックし、カスタムの色を定義して使用します。  
  
-   **[オブジェクト エクスプローラー]** ペインのサーバー エントリの色を指定すると、クエリ エディター ウィンドウを開いたときにその色が使用されます。 クエリ エディター ウィンドウを開くには、サーバー エントリを右クリックし、 **[新しいクエリ]** を選択します。または、 **[オブジェクト エクスプローラー]** ペインがアクティブで、このサーバーにフォーカスが置かれている場合は、ツール バーの **[新しいクエリ]** をクリックします。  
  
-   **[登録済みサーバー]** ペインのサーバー エントリの色を指定すると、クエリ エディター ウィンドウを開いたときにその色が使用されます。 クエリ エディター ウィンドウを開くには、サーバー エントリを右クリックし、 **[新しいクエリ]** を選択します。または、 **[登録済みサーバー]** ペインがアクティブで、このサーバーにフォーカスが置かれている場合は、ツール バーの **[新しいクエリ]** をクリックします。  
  
-   **[ファイル]** メニューで、 **[新規作成]** 、 **[データベース エンジン クエリ]** の順にクリックすると、 **[サーバーへの接続]** ダイアログ ボックスで指定した色がそのクエリ エディター ウィンドウに適用されます。  
  
 **[すべてリセット]**  
 手動で入力された接続プロパティ値をすべて既定値に置き換えます。  
  
 **のインスタンスに接続するときには、**  
 一覧表示された値を使用して接続を試行します。  
  
 **および**  
 クリックすると、ダイアログ ボックスが切り替わり、パスワードの保存などの追加のサーバー接続オプションが非表示になります。  
  
 **を登録するときには、**  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] を **登録済みサーバー**に登録するときに、クリックして接続をテストします。  
  
 **および**  
 **登録済みサーバー**に設定を保存します。  
  
## <a name="see-also"></a>参照  
 [[接続プロパティ] ダイアログ ボックス](../../database-engine/connection-properties-dialog-box.md)  
  
  