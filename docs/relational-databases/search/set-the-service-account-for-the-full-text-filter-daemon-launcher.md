---
title: "フルテキスト フィルター デーモン ランチャーのサービス アカウントの設定 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-search"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "フルテキスト検索 [SQL Server], FDHOST ランチャー (MSSQLFDLauncher) サービス アカウント"
  - "FDHOST ランチャー (MSSQLFDLauncher) [SQL Server]"
ms.assetid: 3ab1d101-7ae0-488f-9b57-468e2517b737
caps.latest.revision: 50
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 49
---
# フルテキスト フィルター デーモン ランチャーのサービス アカウントの設定
  このトピックでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを使用して、SQL フルテキスト フィルター デーモン ランチャー サービス (MSSQLFDLauncher) のサービス アカウントを設定する方法について説明します。 SQL フルテキスト フィルター デーモン ランチャー サービスは、ssNoVersion のフルテキスト検索でフィルター処理や単語区切りを行うフィルター デーモン ホスト プロセスを開始するために使用されます。 フルテキスト検索を使用するには、このサービスが実行されている必要があります。  
  
 SQL フルテキスト フィルター デーモン ランチャー サービスは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の特定のインスタンスに関連付けられているインスタンス対応のサービスです。 SQL フルテキスト フィルター デーモン ランチャー サービスにより、各フィルター デーモン ホスト プロセスにサービス アカウント情報が反映されます。  
  
##  <a name="TOP"></a> このセクションの内容  
  
-   [セキュリティに関する推奨事項](#rec)  
  
-   [サービス アカウントの設定](#setting)  
  
-   [SQL フルテキスト フィルター デーモン ランチャー サービスが起動しない場合](#error)  
  
##  <a name="setting"></a> サービス アカウントの設定  
  
#### フルテキスト検索の SQL フルテキスト フィルター デーモン ランチャー サービス アカウントを設定するには  
  
1.  **[スタート]** メニューで、 **[すべてのプログラム]**、[ [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]]、 **[構成ツール]**の順にポイントして、 **[SQL Server 構成マネージャー]**をクリックします。  
  
2.  **[SQL Server 構成マネージャー]** で、**[SQL Server のサービス]** をクリックし、**[SQL フルテキスト フィルター デーモン ランチャー (***インスタンス名***)]** を右クリックし、**[プロパティ]** をクリックします。  
  
3.  ダイアログ ボックスの **[ログオン]** タブをクリックし、SQL フルテキスト フィルター デーモン ランチャー サービスによって作成される各プロセスについて、その実行に使用するアカウントを選択または入力します。  
  
4.  ダイアログ ボックスを閉じた後、**[再起動]** をクリックすると、SQL フルテキスト フィルター デーモン ランチャー サービスが再起動されます。  
  
 [このセクションの内容](#TOP)  
  
##  <a name="error"></a> SQL フルテキスト フィルター デーモン ランチャー サービスが起動しない場合  
 SQL フルテキスト フィルター デーモン ランチャー サービスが開始されない場合は、次の原因が考えられます。  
  
-   SQL フルテキスト フィルター デーモン ランチャー サービスのアカウントに関連付けられたパスワードの期限が切れている。  
  
     SQL フルテキスト フィルター デーモン ランチャー サービスにローカル ユーザー アカウントを使用している場合にパスワードの期限が切れたときは、次の作業を行う必要があります。  
  
    1.  アカウントに新しい Windows パスワードを設定します。  
  
    2.  新しいパスワードが使用されるように、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーで SQL フルテキスト フィルター デーモン ランチャー サービスを更新します。  
  
-   サービス アカウントのユーザー アカウントまたはパスワードが正しくない。  
  
     SQL フルテキスト フィルター デーモン ランチャー サービスが、正しくないユーザー アカウントおよびパスワードでログインしようとしている可能性があります。 上記の手順に従って、サービスのユーザー アカウントが変更されていないことを確認してください。  
  
-   サービスへのログインに使用されるアカウントに権限がない。  
  
     サーバー インスタンスがインストールされているコンピューターに対するログイン権限のないアカウントを使用している可能性があります。 ローカル コンピューターのユーザー権利および権限を持つアカウントでログインしていることを確認してください。  
  
-   同じ名前付きパイプの別のインスタンスが既に実行されている。  
  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスは、SQL フルテキスト フィルター デーモン ランチャー サービス クライアントの名前付きパイプ サーバーとして機能します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が開始される前に名前付きパイプが別のプロセスで作成されていると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログと Windows イベント ログにエラーが記録され、フルテキスト検索を使用できません。  同じ名前付きパイプを使用しようとしているプロセスまたはアプリケーションを特定し、そのアプリケーションを停止してください。  
  
-   フルテキスト検索で SQL フルテキスト フィルター デーモン ランチャー サービスが正しく構成されていない。  
  
     サービスが、ローカル コンピューターで正しく構成されていない可能性があります。  
  
     名前付きパイプの機能がローカル コンピューターで無効になっているか、既定の名前付きパイプ以外の名前付きパイプを使用するように [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が構成されていると、SQL フルテキスト フィルター デーモン ランチャー サービスが開始されないことがあります。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス グループに、SQL フルテキスト フィルター デーモン ランチャー サービスを開始する権限がない。  
  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストール時、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス グループには、SQL フルテキスト フィルター デーモン ランチャー サービスを管理、クエリ、および開始する既定の権限が与えられます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストール後に SQL フルテキスト フィルター デーモン ランチャー サービス アカウントに対する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス グループの権限が削除されている場合、SQL フルテキスト フィルター デーモン ランチャー サービスは開始されず、フルテキスト検索は無効になります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス グループに、SQL フルテキスト フィルター デーモン ランチャー サービス アカウントに対する権限があることを確認してください。  
  
 [このセクションの内容](#TOP)  
  
## 参照  
 [サービスの管理方法に関するトピック &#40;SQL Server 構成マネージャー&#41;](../Topic/Managing%20Services%20How-to%20Topics%20\(SQL%20Server%20Configuration%20Manager\).md)   
 [フルテキスト検索のアップグレード](../../relational-databases/search/upgrade-full-text-search.md)  
  
  