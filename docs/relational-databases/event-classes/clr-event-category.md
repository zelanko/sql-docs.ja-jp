---
title: "CLR イベント カテゴリ | Microsoft Docs"
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
  - "イベント クラス [SQL Server], CLR イベント カテゴリ"
  - "SQL Server イベント クラス, CLR イベント カテゴリ"
  - "CLR イベント カテゴリ [SQL Server]"
ms.assetid: a7c0cd60-3bec-42be-ad5e-473bd26a06d9
caps.latest.revision: 17
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 17
---
# CLR イベント カテゴリ
  **CLR** イベント カテゴリには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内で [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 共通言語ランタイム (CLR) オブジェクトを実行すると生成されるイベント クラスが含まれます。  
 
 ## Assembly Load イベント クラス 
  **Assembly Load** イベント クラスは、アセンブリの読み込み要求が実行されるときに発生します。  
  
 アセンブリの読み込みを監視するトレースに **Assembly Load** イベント クラスを含めます。 これは、共通言語ランタイム (CLR) を使用するクエリのトラブルシューティングを行う場合、CLR クエリが実行されているサーバーの実行速度の低下のトラブルシューティングを行う場合、アセンブリの読み込みに関してユーザー、データベース、成功、またはその他の情報を収集するためにサーバーを監視する場合に役に立ちます。  
  
## Assembly Load イベント クラスのデータ列  
  
|データ列名|データ型|説明|列 ID|フィルターの適用|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|**nvarchar**|読み込みを要求したアプリケーションの名前。|10|はい|  
|**ClientProcessID**|**int**|クライアント アプリケーションが実行されているプロセスに対し、ホスト コンピューターが割り当てた ID。 クライアントによりクライアント プロセス ID が指定されると、このデータ列に値が格納されます。|9|はい|  
|**DatabaseID**|**int**|USE database ステートメントで指定されたデータベースの ID、または特定のインスタンスについて USE database ステートメントが実行されていない場合は既定のデータベースの ID となります。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] では、 **ServerName** データ列がトレースにキャプチャされ、そのサーバーが利用可能な場合、データベースの名前が表示されます。 データベースに対応する値は、DB_ID 関数を使用して特定します。|3|可|  
|**DatabaseName**|**nvarchar**|ユーザーのステートメントが実行されているデータベースの名前。|35|可|  
|**EventSequence**|**int**|要求内の特定のイベントのシーケンス。|51|いいえ|  
|**GroupID**|**int**|SQL トレース イベントが発生したワークロード グループの ID。|66|はい|  
|**HostName**|**nvarchar**|クライアントが実行されているコンピューターの名前。 このデータ列にはクライアントからホスト名が提供されている場合に値が格納されます。 ホスト名を指定するには、HOST_NAME 関数を使用します。|8|はい|  
|**LoginName**|**nvarchar**|ユーザーのログイン名 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セキュリティ ログインまたは DOMAIN\username という形式の [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ログイン資格情報)。|11|はい|  
|**LoginSID**|**image**|ログインしたユーザーのセキュリティ識別子 (SID)。 この情報は、**sys.server_principals** カタログ ビューで参照できます。 各 SID はサーバーのログインごとに一意です。|41|可|  
|**NTDomainName**|**nvarchar**|ユーザーが所属する Windows ドメイン。|7|はい|  
|**NTUserName**|**nvarchar**|Windows のユーザー名。|6|可|  
|**ObjectID**|**int**|アセンブリ ID。|22|はい|  
|**ObjectName**|**nvarchar**|アセンブリの完全修飾名。|34|可|  
|**RequestID**|**int**|ステートメントが含まれている要求の ID。|49|可|  
|**ServerName**|**nvarchar**|トレースされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの名前。|26|不可|  
|**SessionLoginName**|**nvarchar**|セッションを開始したユーザーのログイン名。 たとえば、Login1 を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、Login2 でステートメントを実行すると、 **SessionLoginName** には Login1 が表示され、 **LoginName** には Login2 が表示されます。 この列には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインと Windows ログインの両方が表示されます。|64|可|  
|**SPID**|**int**|イベントが発生したセッションの ID。|12|はい|  
|**StartTime**|**datetime**|イベントの開始時刻 (取得できた場合)。|14|可|  
|**成功**|**int**|アセンブリの読み込みの成功 (1) または失敗 (0) を示します。|23|可|  
|**TextData**|**ntext**|読み込みが成功した場合は "アセンブリの読み込み成功" が、それ以外の場合は "アセンブリの読み込み失敗"。|1|はい|  
  
## 参照  
 [拡張イベント](../../relational-databases/extended-events/extended-events.md)   
 [アセンブリ &#40;データベース エンジン&#41;](../../relational-databases/clr-integration/assemblies-database-engine.md)  
  
   
  
## 参照  
 [拡張イベント](../../relational-databases/extended-events/extended-events.md)  
  
  