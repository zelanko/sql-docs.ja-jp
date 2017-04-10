---
title: "SP:Recompile イベント クラス | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SP:Recompile イベント クラス"
ms.assetid: 526c8eae-a07b-4d0e-b91e-8e537835d77d
caps.latest.revision: 43
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 43
---
# SP:Recompile イベント クラス
  SP:Recompile イベント クラスは、ストアド プロシージャ、トリガー、またはユーザー定義関数が再コンパイルされたことを示します。 このイベント クラスから報告される再コンパイルは、ステートメント レベルで発生します。  
  
 ステートメント レベルの再コンパイルを追跡する方法としては、SQL:StmtRecompile イベント クラスの使用をお勧めします。 SP:Recompile イベント クラスの使用が推奨されなくなりました。 詳細については、「[SQL:StmtRecompile イベント クラス](../../relational-databases/event-classes/sql-stmtrecompile-event-class.md)」を参照してください。  
  
## SP:Recompile イベント クラスのデータ列  
  
|データ列名|**データ型**|説明|列 ID|フィルターの適用|  
|----------------------|-------------------|-----------------|---------------|----------------|  
|ApplicationName|**nvarchar**| [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスへの接続を作成したクライアント アプリケーションの名前。 この列には、プログラムの表示名ではなく、アプリケーションによって渡された値が格納されます。|10|はい|  
|ClientProcessID|**int**|クライアント アプリケーションが実行されているプロセスに対し、ホスト コンピューターが割り当てた ID。 クライアントによりプロセス ID が指定されている場合は、このデータ列に値が格納されます。|9|はい|  
|DatabaseID|**int**|ストアド プロシージャが実行されているデータベースの ID。 データベースに対応する値は、DB_ID 関数を使用して特定します。|3|可|  
|DatabaseName|**nvarchar**|ストアド プロシージャが実行されているデータベースの名前。|35|可|  
|EventClass|**int**|イベントの種類 = 37。|27|いいえ|  
|EventSequence|**int**|要求内の特定のイベントのシーケンス。|51|不可|  
|EventSubClass|**int**|イベント サブクラスの種類。 再コンパイルの理由を示します。<br /><br /> 1 = スキーマの変更<br /><br /> 2 = 統計の変更<br /><br /> 3 = DNR による再コンパイル<br /><br /> 4 = 設定オプションの変更<br /><br /> 5 = 一時テーブルの変更<br /><br /> 6 = リモート行セットの変更<br /><br /> 7 = ブラウズ権限の変更<br /><br /> 8 = クエリ通知環境の変更<br /><br /> 9 = MPI ビューの変更<br /><br /> 10 = カーソル オプションの変更<br /><br /> 11 = 再コンパイル オプションあり|21|可|  
|GroupID|**int**|SQL トレース イベントが発生したワークロード グループの ID。|66|はい|  
|HostName|**nvarchar**|クライアントが実行されているコンピューターの名前。 このデータ列にはクライアントからホスト名が提供されている場合に値が格納されます。 ホスト名を指定するには、HOST_NAME 関数を使用します。|8|可|  
|IntegerData2|**int**|再コンパイルの原因となったストアド プロシージャまたはバッチ内のステートメントの終了オフセット。 ステートメントがそのバッチの最後のステートメントである場合、終了オフセットは -1 です。|55|はい|  
|IsSystem|**int**|イベントがシステム プロセスとユーザー プロセスのどちらで発生したか。 1 はシステム、0 はユーザーです。|60|可|  
|LoginName|**nvarchar**|ユーザーのログイン名 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セキュリティ ログインまたは DOMAIN\username という形式の [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ログイン資格情報)。|11|可|  
|LoginSid|**image**|ログイン ユーザーのセキュリティ ID 番号 (SID)。 この情報は、sys.server_principals カタログ ビューで参照できます。 各 SID はサーバーのログインごとに一意です。|41|はい|  
|NestLevel|**int**|ストアド プロシージャの入れ子のレベル。|29|可|  
|NTDomainName|**nvarchar**|ユーザーが所属する Windows ドメイン。|7|はい|  
|NTUserName|**nvarchar**|Windows のユーザー名。|6|可|  
|ObjectID|**int**|ストアド プロシージャにシステムが割り当てた ID。|22|はい|  
|ObjectName|**nvarchar**|再コンパイルを発生させたオブジェクトの名前。|34|可|  
|ObjectType|**int**|イベントに関係するオブジェクトの種類を表す値。 詳細については、「[ObjectType トレース イベント列](../../relational-databases/event-classes/objecttype-trace-event-column.md)」を参照してください。|28|はい|  
|Offset|**int**|再コンパイルの原因となったストアド プロシージャまたはバッチ内のステートメントの開始オフセット。|61|はい|  
|RequestID|**int**|ステートメントが含まれている要求の ID。|49|可|  
|ServerName|**nvarchar**|トレースされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの名前。|26|不可|  
|SessionLoginName|**nvarchar**|セッションを開始したユーザーのログイン名。 たとえば、Login1 を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、Login2 でステートメントを実行すると、SessionLoginName には Login1 が表示され、LoginName には Login2 が表示されます。 この列には、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインと Windows ログインの両方が表示されます。|64|可|  
|SPID|**int**|イベントが発生したセッションの ID。|12|はい|  
|SqlHandle|**varbinary**|64 ビット ハッシュ。アドホック クエリやデータベースのテキスト、および SQL オブジェクトのオブジェクト ID に基づいています。 この値を sys.dm_exec_sql_text に渡して、関連付けられている SQL テキストを取得できます。|63|はい|  
|StartTime|**datetime**|イベントの開始時刻 (取得できた場合)。|14|はい|  
|TextData|**ntext**|ステートメントレベルの再コンパイルの原因となった Transact-SQL ステートメントのテキスト。|1|可|  
|TransactionID|**bigint**|システムによって割り当てられたトランザクション ID。|4|可|  
|XactSequence|**bigint**|現在のトランザクションを説明するトークン。|50|はい|  
  
## 参照  
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [SQL:StmtRecompile イベント クラス](../../relational-databases/event-classes/sql-stmtrecompile-event-class.md)  
  
  