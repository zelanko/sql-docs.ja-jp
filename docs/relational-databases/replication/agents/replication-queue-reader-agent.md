---
title: "レプリケーション キュー リーダー エージェント | Microsoft Docs"
ms.custom: ""
ms.date: "06/02/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エージェント [SQL Server レプリケーション], キュー リーダー エージェント"
  - "コマンド ライン プロンプト [SQL Server レプリケーション]"
  - "キュー リーダー エージェント, パラメーター参照"
  - "キュー リーダー エージェント, 実行可能ファイル"
ms.assetid: 8e227793-11f6-47c6-99dc-ffc282f5d4bf
caps.latest.revision: 36
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 36
---
# レプリケーション キュー リーダー エージェント
  レプリケーション キュー リーダー エージェントが実行可能ファイルに格納されているメッセージを読み取る、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] キューまたは [!INCLUDE[msCoName](../../../includes/msconame-md.md)] メッセージ キューし、それらのメッセージをパブリッシャーに適用します。 キュー リーダー エージェントは、スナップショット、およびキュー更新を許可するトランザクション パブリケーションで使用されます。  
  
> [!NOTE]  
>  パラメーターは任意の順序で指定できます。 オプション パラメーターを指定しなかった場合、既定のエージェント プロファイルの定義済みの値が使用されます。  
  
## 構文  
  
```  
  
qrdrsvc [-?]  
[-Continuous]  
[-DefinitionFile definition_file]  
[-Distributor server_name[\instance_name]]  
[-DistributionDB distribution_database]  
[-DistributorLogin distributor_login]  
[-DistributorPassword distributor_password]  
[-DistributorSecurityMode [0|1]]  
[-EncryptionLevel [0|1|2]]  
[-HistoryVerboseLevel [0|1|2|3]]  
[-LoginTimeOut login_time_out_seconds]  
[-Output output_path_and_file_name]  
[-OutputVerboseLevel [0|1|2]]  
[-PollingInterval polling_interval]  
[-PublisherFailoverPartner server_name[\instance_name] ]  
[-ProfileName agent_profile_name]  
[-QueryTimeOut query_time_out_seconds]  
[-ResolverState [1|2|3]]  
```  
  
## 引数  
 **-?**  
 使用方法についての情報を表示します。  
  
 **-Continuous**  
 キューに格納されたトランザクションの処理を、エージェントが継続的に試みるかどうかを指定します。 指定した場合、エージェントは、サブスクライバーから受け取った保留中のトランザクションがキューに存在しない場合でも、実行を継続します。  
  
 **-Definitionfile** *def_path_and_file_name*  
 エージェント定義ファイルのパスです。 エージェント定義ファイルには、エージェントのコマンド ライン引数が含まれます。 ファイルの内容は実行可能ファイルとして解析されます。 二重引用符 (") を使用して、任意の文字を含む引数値を指定します。  
  
 **-ディストリビューター** *server_name*[**\\***instance_name*]  
 ディストリビューターの名前です。 指定 *server_name* の既定のインスタンスの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] そのサーバーにします。 指定 *server_name*\\*instance_name* の名前付きインスタンスの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] そのサーバーにします。 指定しなかった場合、既定値はローカル コンピューターの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の既定のインスタンスの名前になります。  
  
 **-DistributionDB** *distribution_database*  
 ディストリビューション データベース名です。  
  
 **-Distributorlogin** *distributor_login*  
 ディストリビューターのログイン名です。  
  
 **-Distributorpassword** *distributor_password 用途*  
 ディストリビューターのパスワードです。  
  
 **-Distributorsecuritymode** [ **0**| **1**]  
 ディストリビューターのセキュリティ モードを指定します。 値 **0** 示す [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証モード (既定)、および値の **1** Windows 認証モードを示します。  
  
 **-Encryptionlevel** [ **0** | **1** | **2** ]  
 接続確立時にキュー リーダー エージェントが使用する SSL (Secure Sockets Layer) の暗号化レベルです。  
  
|EncryptionLevel の値|説明|  
|---------------------------|-----------------|  
|**0**|SSL は使用されません。|  
|**1**|SSL は使用されますが、信頼できる発行者によって SSL サーバー証明が署名されているかどうかを検証しません。|  
|**2**|SSL が使用され、証明書の確認が行われます。|  
  
 詳細については、次を参照してください。 [セキュリティの概要と #40 です。レプリケーションと #41;](../../../relational-databases/replication/security/security-overview-replication.md)します。  
  
 **-Historyverboselevel** [ **0**| **1**| **2**| **3**]  
 キュー リーダー操作中にログに記録する履歴の量を指定します。 履歴を選択してログのパフォーマンスへの影響を最小限に抑えることができます **1**します。  
  
|HistoryVerboseLevel の値|説明|  
|-------------------------------|-----------------|  
|**0**|履歴はログに記録されません。この設定はお勧めできません。|  
|**1**|既定値です。 同じ状態 (startup、progress、success など) を示している以前の履歴メッセージを常に更新します。 前回の記録に同じ状態がない場合は、新しい記録を挿入します。|  
|**2**|アイドル状態のメッセージや長時間実行されるジョブのメッセージを含む新しい履歴レコードを挿入します。|  
|**3**|トラブルシューティングに役立つ補足的な情報を含む新しい履歴レコードを挿入します。|  
  
 **-Logintimeout** *login_time_out_seconds*  
 ログインがタイムアウトになるまでの秒数です。 既定値は 15 秒です。  
  
 **-出力** *output_path_and_file_name*  
 エージェントの出力ファイルのパスです。 ファイル名が指定されていない場合、出力はコンソールに送られます。 指定された名前のファイルが存在する場合、出力はそのファイルに追加されます。  
  
 **-Outputverboselevel** [ **0**| **1**| **2**]  
 出力を詳細表示にするかどうかを指定します。 詳細レベルが **0**の場合、エラー メッセージだけが出力されます。 詳細レベルが **1**の場合、すべての実行状況報告メッセージが出力されます。 詳細レベルが場合 **2** (既定)、すべてのエラー メッセージと進行状況レポート メッセージが出力されます。 これはデバッグに役立ちます。  
  
 **-PollingInterval** *polling_interval*  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ベースのキューを使用したサブスクリプションの更新時にのみ適用されます。 保留中のトランザクションがキューに格納されているかどうかを確認するために、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のキューをポーリングする頻度を秒数で指定します。 有効値は、0 ～ 240 秒です。 既定値は 5 秒です。  
  
 **-PublisherFailoverPartner** *server_name*[**\\***instance_name*]  
 パブリケーション データベースとのデータベース ミラーリング セッションに参加する、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フェールオーバー パートナー インスタンスを指定します。 詳細については、次を参照してください。 [データベース ミラーリングとレプリケーション/#40 です。SQL Server と #41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md)します。  
  
 **-ProfileName** *agent_profile_name*  
 エージェントに対して既定値を提供するエージェント プロファイルの名前です。 詳細については、次を参照してください。 [レプリケーション エージェント プロファイル](../../../relational-databases/replication/agents/replication-agent-profiles.md)します。  
  
 **-Querytimeout** *query_time_out_seconds*  
 クエリがタイムアウトになるまでの秒数です。 既定値は 1800 秒です。  
  
 **-Resolverstate** [ **1**| **2**| **3**]  
 キュー更新における競合の解決方法を指定します。 値 **1** パブリッシャー優先を競合と現在のキューに置かれたトランザクションは、パブリッシャーと元の更新サブスクライバーでロールバックされます。 後続のキューに置かれたトランザクションの処理は続行されます競合していることを示します。 値 **2** を示し、サブスクライバーが優先されるキューに置かれたトランザクションがパブリッシャーの値よりも優先されます。 値 **3** ことを示しサブスクライバーが再初期化で、競合が発生;、パブリッシャーを優先、後続のキューに置かれたトランザクションの処理が終了する、サブスクリプションは再初期化します。 既定の設定は **1** のトランザクション パブリケーションと **3** スナップショット パブリケーションの場合。  
  
## 解説  
 キュー リーダー エージェントを開始するには、実行 **qrdrsvc.exe** コマンド プロンプトからです。 詳細については、次を参照してください。 [レプリケーション エージェント実行可能ファイル](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)します。  
  
## 参照  
 [レプリケーション エージェントの管理](../../../relational-databases/replication/agents/replication-agent-administration.md)  
  
  