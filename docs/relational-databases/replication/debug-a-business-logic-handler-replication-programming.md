---
title: "ビジネス ロジック ハンドラーのデバッグ (レプリケーション プログラミング) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "マージ レプリケーションのビジネス ロジック ハンドラー [SQL Server レプリケーション]"
  - "ビジネス ロジック ハンドラー [SQL Server レプリケーション]"
  - "BusinessLogicModule クラス"
ms.assetid: edd0d17a-0e9c-4c28-8395-a7d47e8ce3d6
caps.latest.revision: 34
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 34
---
# ビジネス ロジック ハンドラーのデバッグ (レプリケーション プログラミング)
  マージ サブスクリプションの同期時にカスタム ビジネス ロジックを呼び出すには、ビジネス ロジック ハンドラーを使用します。 詳細については、次を参照してください。 [マージ同期中にビジネス ロジックを実行](../../relational-databases/replication/merge/execute-business-logic-during-merge-synchronization.md)します。  
  
 マージ レプリケーション競合回避モジュール (replrec.dll) は、ビジネス ロジックを含むマネージ コード アセンブリを呼び出します。 ほとんどの場合、replrec.dll とカスタム ビジネス ロジックは、マージ エージェントが実行されるコンピューター (プル サブスクリプションの場合はサブスクライバー、プッシュ サブスクリプションの場合はディストリビューター) で実行されます。 Web 同期の場合、または [!INCLUDE[ssEW](../../includes/ssew-md.md)] サブスクライバーの場合、競合回避モジュールとカスタム ビジネス ロジックは Web サーバーで実行されます。  
  
### ローカル コンピューターでビジネス ロジック ハンドラーをデバッグするには  
  
1.  パブリッシングとディストリビューションを構成し、パブリケーションを作成し、パブリケーションへのサブスクリプションを作成します。 詳細については、次を参照してください。 [パブリッシングとディストリビューション](../../relational-databases/replication/configure-publishing-and-distribution.md) と [作成、変更、およびパブリケーションの削除と記事 & #40 です。レプリケーションと #41;](../../relational-databases/replication/publish/create-modify-and-delete-publications-and-articles-replication.md)します。  
  
2.  ビジネス ロジック ハンドラーを作成して登録します。 詳しくは、「 [Implement a Business Logic Handler for a Merge Article](../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)」をご覧ください。  
  
3.  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio で、マージ エージェントをプログラムで同期的に起動するレプリケーション管理オブジェクト (RMO) プロジェクトを作成します。 詳しくは、「 [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md)」をご覧ください。  
  
4.  ビジネス ロジック ハンドラー コードのデバッグ対象のメソッドまたはクラス コンストラクター内にブレークポイントを設定します。 ビジネス ロジック ハンドラーに実装できる方法の詳細については、次を参照してください。、 <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> メソッドのトピックです。  
  
5.  ビジネス ロジック ハンドラーをデバッグ モードでビルドし、手順 1. で登録した場所にアセンブリとデバッグ シンボル ファイル (.pdb) を配置します。  
  
    > [!NOTE]  
    >  デバッグを簡素化するには、ビジネス ロジック ハンドラー プロジェクトとサブスクリプションを同期するプロジェクトの両方を含む単一の Visual Studio .NET ソリューションを作成します。 その場合は、同期プロジェクトをスタートアップ プロジェクトとして設定し、デバッグ時に手順 1. で登録した場所にビジネス ロジック アセンブリを配置するようにビルド環境を構成します。  
  
6.  サブスクリプションまたはパブリケーション データベースに対して、挿入、更新、削除のいずれかのコマンドを実行します。 コマンドと実行場所は、デバッグ対象のメソッドによって異なります。  
  
7.  手順 3. のプロジェクトをデバッグ モードで起動し、サブスクリプションを同期します。  
  
8.  他のブレークポイントを設定しておらず、適切なコマンドがレプリケートされたと仮定すると、ビジネス ロジック ハンドラー内のブレークポイントに達したときに実行が停止します。  
  
### Web 同期を使用する Web サーバーまたは SQL Server Compact サブスクライバーに対してビジネス ロジック ハンドラーをデバッグするには  
  
1.  パブリッシングとディストリビューションを構成し、パブリケーションを作成し、パブリケーションへのプル サブスクリプションを作成します。 パブリケーションは、Web 同期をサポートする必要がありますか [!INCLUDE[ssEW](../../includes/ssew-md.md)] サブスクライバーです。  
  
2.  ビジネス ロジック ハンドラーを作成して登録します。 詳しくは、「 [Implement a Business Logic Handler for a Merge Article](../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)」をご覧ください。  
  
3.  ビジネス ロジック ハンドラー コードのデバッグ対象のメソッドまたはクラス コンストラクター内にブレークポイントを設定します。 ビジネス ロジック ハンドラーに実装できる方法の詳細については、次を参照してください。、 <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> メソッドのトピックです。  
  
4.  ビジネス ロジック ハンドラーをデバッグ モードでビルドし、手順 1. で登録した場所にある Web サーバーにアセンブリとデバッグ シンボル ファイル (.pdb) を配置します。  
  
    > [!NOTE]  
    >  アセンブリが使用中であるためにビジネス ロジック ハンドラーのビルドに失敗した場合は、Web サーバーでコマンド プロンプトからコマンド `iisreset` を入力し、Web サーバーをリセットします。  
  
5.  Web 同期を有効にしてサブスクリプションを同期します。 同期中に、Web サーバーは登録されたアセンブリを読み込みます。  
  
6.  Visual Studio .NET デバッガーを使用し、Web サーバー上の以下のプロセスのいずれかにアタッチします。  
  
    -   w3wp.exe - Windows Server 2003。  
  
    -   inetinfo.exe - Windows 2000 および Windows XP。  
  
7.   **出力** ウィンドウで確認して、デバッグ出力を登録済みのアセンブリのシンボルが正しく読み込まれていることを確認します。 シンボルが読み込まれていない場合は、適切な .pdb ファイルが手順 4. でコピーされたことを確認し、手順 5. を繰り返します。  
  
8.  サブスクリプションまたはパブリケーション データベースに対して、挿入、更新、削除のいずれかのコマンドを実行します。 コマンドと実行場所は、デバッグ対象のメソッドによって異なります。  
  
9. Visual Studio デバッガーを使用し、w3wp.exe プロセスにアタッチします。  
  
10. Web 同期を使用して、サブスクリプションを再び同期します。  
  
11. 他のブレークポイントを設定しておらず、適切なコマンドがレプリケートされたと仮定すると、ビジネス ロジック ハンドラー内のブレークポイントに達したときに実行が停止します。  
  
## 参照  
 [マージ アーティクルのビジネス ロジック ハンドラーの実装](../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)  
  
  