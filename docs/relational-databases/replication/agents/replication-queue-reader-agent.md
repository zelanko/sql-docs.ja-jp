---
title: "レプリケーション キュー リーダー エージェント | Microsoft Docs"
ms.custom: 
ms.date: 06/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- agents [SQL Server replication], Queue Reader Agent
- command prompt [SQL Server replication]
- Queue Reader Agent, parameter reference
- Queue Reader Agent, executables
ms.assetid: 8e227793-11f6-47c6-99dc-ffc282f5d4bf
caps.latest.revision: "36"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9a0c0fcae1a5f2a63a40da76bfb3e676f03d96fd
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="replication-queue-reader-agent"></a>レプリケーション キュー リーダー エージェント
  レプリケーション キュー リーダー エージェントは、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のキューまたは [!INCLUDE[msCoName](../../../includes/msconame-md.md)] のメッセージ キューに格納されたメッセージを読み取り、これらのメッセージをパブリッシャーに適用する実行可能ファイルです。 キュー リーダー エージェントは、スナップショット、およびキュー更新を許可するトランザクション パブリケーションで使用されます。  
  
> [!NOTE]  
>  パラメーターは任意の順序で指定できます。 オプション パラメーターを指定しなかった場合、既定のエージェント プロファイルの定義済みの値が使用されます。  
  
## <a name="syntax"></a>構文  
  
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
  
## <a name="arguments"></a>引数  
 **-?**  
 使用方法についての情報を表示します。  
  
 **-Continuous**  
 キューに格納されたトランザクションの処理を、エージェントが継続的に試みるかどうかを指定します。 指定した場合、エージェントは、サブスクライバーから受け取った保留中のトランザクションがキューに存在しない場合でも、実行を継続します。  
  
 **-DefinitionFile** *def_path_and_file_name*  
 エージェント定義ファイルのパスです。 エージェント定義ファイルには、エージェントのコマンド ライン引数が含まれます。 ファイルの内容は実行可能ファイルとして解析されます。 二重引用符 (") を使用して、任意の文字を含む引数値を指定します。  
  
 **-Distributor** *server_name*[**\\***instance_name*]  
 ディストリビューターの名前です。 サーバー上の *の既定のインスタンスの場合は、* server_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を指定します。 サーバー上の *server_name*\\*instance_name* instance_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を指定します。 指定しなかった場合、既定値はローカル コンピューターの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の既定のインスタンスの名前になります。  
  
 **-DistributionDB** *distribution_database*  
 ディストリビューション データベース名です。  
  
 **-DistributorLogin** *distributor_login*  
 ディストリビューターのログイン名です。  
  
 **-DistributorPassword** *distributor_password*  
 ディストリビューターのパスワードです。  
  
 **-DistributorSecurityMode** [ **0**| **1**]  
 ディストリビューターのセキュリティ モードを指定します。 値 **0** は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証モード (既定値) を示し、値 **1** は Windows 認証モードを示します。  
  
 **-EncryptionLevel** [ **0** | **1** | **2** ]  
 接続確立時にキュー リーダー エージェントが使用する SSL (Secure Sockets Layer) の暗号化レベルです。  
  
|EncryptionLevel の値|説明|  
|---------------------------|-----------------|  
|**0**|SSL は使用されません。|  
|**1**|SSL は使用されますが、信頼できる発行者によって SSL サーバー証明が署名されているかどうかを検証しません。|  
|**2**|SSL が使用され、証明書の確認が行われます。|  
  
 詳細については、「[セキュリティの概要 &#40;レプリケーション&#41;](../../../relational-databases/replication/security/security-overview-replication.md)」を参照してください。  
  
 **-HistoryVerboseLevel** [ **0**| **1**| **2**| **3**]  
 キュー リーダー操作中にログに記録する履歴の量を指定します。 **1**を選択すれば、ログへの履歴の記録がパフォーマンスに与える影響を最小限に抑えることができます。  
  
|HistoryVerboseLevel の値|説明|  
|-------------------------------|-----------------|  
|**0**|履歴はログに記録されません。この設定はお勧めできません。|  
|**1**|既定値です。 同じ状態 (startup、progress、success など) を示している以前の履歴メッセージを常に更新します。 前回の記録に同じ状態がない場合は、新しい記録を挿入します。|  
|**2**|アイドル状態のメッセージや長時間実行されるジョブのメッセージを含む新しい履歴レコードを挿入します。|  
|**3**|トラブルシューティングに役立つ補足的な情報を含む新しい履歴レコードを挿入します。|  
  
 **-LoginTimeOut** *login_time_out_seconds*  
 ログインがタイムアウトになるまでの秒数です。既定値は 15 秒です。  
  
 **-Output** *output_path_and_file_name*  
 エージェントの出力ファイルのパスです。 ファイル名が指定されていない場合、出力はコンソールに送られます。 指定された名前のファイルが存在する場合、出力はそのファイルに追加されます。  
  
 **-OutputVerboseLevel** [ **0**| **1**| **2**]  
 出力を詳細表示にするかどうかを指定します。 詳細レベルが **0**の場合、エラー メッセージだけが出力されます。 詳細レベルが **1**の場合、すべての実行状況報告メッセージが出力されます。 詳細レベルが **2** (既定値) の場合、すべてのエラー メッセージと実行状況報告メッセージが出力されます。これはデバッグ時に便利です。  
  
 **-PollingInterval** *polling_interval*  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ベースのキューを使用したサブスクリプションの更新時にのみ適用されます。 保留中のトランザクションがキューに格納されているかどうかを確認するために、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のキューをポーリングする頻度を秒数で指定します。 有効値は、0 ～ 240 秒です。 既定値は 5 秒です。  
  
 **-PublisherFailoverPartner** *server_name*[**\\***instance_name*]  
 パブリケーション データベースとのデータベース ミラーリング セッションに参加する、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フェールオーバー パートナー インスタンスを指定します。 詳細については、「[データベース ミラーリングとレプリケーション &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md)」を参照してください。  
  
 **-ProfileName** *agent_profile_name*  
 エージェントに対して既定値を提供するエージェント プロファイルの名前です。 詳細については、「[レプリケーション エージェント プロファイル](../../../relational-databases/replication/agents/replication-agent-profiles.md)」を参照してください。  
  
 **-QueryTimeOut** *query_time_out_seconds*  
 クエリがタイムアウトになるまでの秒数です。既定値は 1800 秒です。  
  
 **-ResolverState** [ **1**| **2**| **3**]  
 キュー更新における競合の解決方法を指定します。 **1** はパブリッシャーが優先されることを示します。この場合、現在キューの中で競合しているトランザクションはパブリッシャー側、およびキューを更新しようとしたサブスクライバー側でロールバックされます。キューに格納されている、それ以降のトランザクションについては、処理が継続されます。 **2** はサブスクライバーが優先されることを示します。つまり、キューに格納されたトランザクションの方がパブリッシャー側の値よりも優先されます。 **3** は、競合が発生した場合は常にサブスクライバーが再初期化されることを示します (つまり、パブリッシャーが優先されます)。この場合、キューに格納された後続のトランザクションは強制的に終了され、サブスクリプションが再初期化されます。 既定の設定は、トランザクション パブリケーションの場合は **1** に、スナップショット パブリケーションの場合は **3** になります。  
  
## <a name="remarks"></a>解説  
 キュー リーダー エージェントを起動するには、コマンド プロンプトから **qrdrsvc.exe** を実行します。 詳細については、「 [レプリケーション エージェント実行可能ファイルのプログラミング](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [レプリケーション エージェントの管理](../../../relational-databases/replication/agents/replication-agent-administration.md)  
  
  
