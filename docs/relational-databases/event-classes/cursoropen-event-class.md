---
title: CursorOpen イベント クラス | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- CursorOpen event class
ms.assetid: d39262c0-0035-42fc-b989-7a16ae0c7345
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 47ec9c3f0e96afe8e62940e20c2326ad5200818c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47654330"
---
# <a name="cursoropen-event-class"></a>CursorOpen イベント クラス
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  **CursorOpen** イベント クラスでは、アプリケーション プログラミング インターフェイス (API) のカーソルで発生する、カーソルを開くイベントが示されます。 カーソルを開くイベントは、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] が、カーソルやカーソル オプションに関連する SQL ステートメントを定義し、カーソルを作成した時点で発生します。  
  
 カーソルのパフォーマンスを記録しているトレースに、 **CursorOpen** イベント クラスを含めます。 **CursorOpen** イベント クラスをトレースに含めた場合、発生するオーバーヘッドの量は、トレース中にデータベースに対してカーソルを使用する頻度によって異なります。 カーソルの使用頻度が高い場合は、トレースによってパフォーマンスが大幅に低下する可能性があります。  
  
## <a name="cursoropen-event-class-data-columns"></a>CursorOpen イベント クラスのデータ列  
  
|データ列名|データ型|[説明]|列 ID|フィルターの適用|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|**nvarchar**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスへの接続を作成したクライアント アプリケーションの名前。 この列には、プログラムの表示名ではなく、アプリケーションによって渡された値が格納されます。|10|[ユーザー アカウント制御]|  
|**ClientProcessID**|**int**|クライアント アプリケーションが実行されているプロセスに対し、ホスト コンピューターが割り当てた ID。 クライアントによりクライアント プロセス ID が指定されると、このデータ列に値が格納されます。|9|[ユーザー アカウント制御]|  
|**DatabaseID**|**int**|USE *database* ステートメントで指定されたデータベースの ID、または特定のインスタンスについて USE *database*ステートメントが実行されていない場合は既定のデータベースの ID となります。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] では、 **ServerName** データ列がトレースにキャプチャされ、そのサーバーが利用可能な場合、データベースの名前が表示されます。 データベースに対応する値は、DB_ID 関数を使用して特定します。|3|[ユーザー アカウント制御]|  
|**DatabaseName**|**nvarchar**|ユーザーのステートメントが実行されているデータベースの名前。|35|[ユーザー アカウント制御]|  
|**EventClass**|**int**|記録されるイベントの種類 = 53。|27|いいえ|  
|**EventSequence**|**int**|バッチ内の **CursorOpen** イベント クラスのシーケンス。|51|いいえ|  
|**GroupID**|**int**|SQL トレース イベントが発生したワークロード グループの ID。|66|[ユーザー アカウント制御]|  
|**Handle**|**int**|サーバーとの間で実行を調整するときに ODBC、OLE DB、または DB-Library によって使用される整数。|33|[ユーザー アカウント制御]|  
|**HostName**|**nvarchar**|クライアントが実行されているコンピューターの名前。 このデータ列にはクライアントからホスト名が提供されている場合に値が格納されます。 ホスト名を指定するには、HOST_NAME 関数を使用します。|8|[ユーザー アカウント制御]|  
|**IntegerData**|**int**|カーソルの種類。 値は次のとおりです。<br /><br /> 1 = キー セット<br /><br /> 2 = 動的<br /><br /> 4 = 順方向専用<br /><br /> 8 = 静的<br /><br /> 16 = 高速順方向|25|[ユーザー アカウント制御]|  
|**IsSystem**|**int**|イベントがシステム プロセスとユーザー プロセスのどちらで発生したか。 1 はシステム、0 はユーザーです。|60|[ユーザー アカウント制御]|  
|**LoginName**|**nvarchar**|ユーザーのログイン名 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セキュリティ ログインまたは DOMAIN\username という形式の [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ログイン資格情報)。|11|[ユーザー アカウント制御]|  
|**LoginSid**|**image**|ログインしたユーザーのセキュリティ識別子 (SID)。 この情報は、 **sys.server_principals** カタログ ビューで参照できます。 各 SID はサーバーのログインごとに一意です。|41|[ユーザー アカウント制御]|  
|**NTDomainName**|**nvarchar**|ユーザーが所属する Windows ドメイン。|7|[ユーザー アカウント制御]|  
|**NTUserName**|**nvarchar**|Windows のユーザー名。|6|[ユーザー アカウント制御]|  
|**RequestID**|**int**|カーソルを開いた要求 ID。|49|[ユーザー アカウント制御]|  
|**ServerName**|**nvarchar**|トレースされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの名前。|26|いいえ|  
|**SessionLoginName**|**nvarchar**|セッションを開始したユーザーのログイン名。 たとえば、Login1 を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、Login2 でステートメントを実行すると、 **SessionLoginName** には Login1 が表示され、 **LoginName** には Login2 が表示されます。 この列には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインと Windows ログインの両方が表示されます。|64|[ユーザー アカウント制御]|  
|**SPID**|**int**|イベントが発生したセッションの ID。|12|[ユーザー アカウント制御]|  
|**StartTime**|**datetime**|イベントの開始時刻 (取得できた場合)。|14|[ユーザー アカウント制御]|  
|**TransactionID**|**bigint**|システムによって割り当てられたトランザクション ID。|4|[ユーザー アカウント制御]|  
|**XactSequence**|**bigint**|現在のトランザクションを説明するトークン。|50|[ユーザー アカウント制御]|  
  
## <a name="see-also"></a>参照  
 [拡張イベント](../../relational-databases/extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [カーソル](../../relational-databases/cursors.md)  
  
  
