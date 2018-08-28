---
title: SP:Recompile イベント クラス | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SP:Recompile event class
ms.assetid: 526c8eae-a07b-4d0e-b91e-8e537835d77d
caps.latest.revision: 43
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 5d00ed434b9a89151cf1bc26df12bb51eda15d79
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43082274"
---
# <a name="sprecompile-event-class"></a>SP:Recompile イベント クラス
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  SP:Recompile イベント クラスは、ストアド プロシージャ、トリガー、またはユーザー定義関数が再コンパイルされたことを示します。 このイベント クラスから報告される再コンパイルは、ステートメント レベルで発生します。  
  
 ステートメント レベルの再コンパイルを追跡する方法としては、SQL:StmtRecompile イベント クラスの使用をお勧めします。 SP:Recompile イベント クラスの使用が非推奨となりました。 詳細については、「 [SQL:StmtRecompile イベント クラス](../../relational-databases/event-classes/sql-stmtrecompile-event-class.md)」を参照してください。  
  
## <a name="sprecompile-event-class-data-columns"></a>SP:Recompile イベント クラスのデータ列  
  
|データ列名|**データ型**|[説明]|列 ID|フィルターの適用|  
|----------------------|-------------------|-----------------|---------------|----------------|  
|ApplicationName|**nvarchar**|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスへの接続を作成したクライアント アプリケーションの名前。 この列には、プログラムの表示名ではなく、アプリケーションによって渡された値が格納されます。|10|[ユーザー アカウント制御]|  
|ClientProcessID|**int**|クライアント アプリケーションが実行されているプロセスに対し、ホスト コンピューターが割り当てた ID。 クライアントによりプロセス ID が指定されている場合は、このデータ列に値が格納されます。|9|[ユーザー アカウント制御]|  
|DatabaseID|**int**|ストアド プロシージャが実行されているデータベースの ID。 データベースに対応する値は、DB_ID 関数を使用して特定します。|3|[ユーザー アカウント制御]|  
|DatabaseName|**nvarchar**|ストアド プロシージャが実行されているデータベースの名前。|35|[ユーザー アカウント制御]|  
|EventClass|**int**|イベントの種類 = 37。|27|いいえ|  
|EventSequence|**int**|要求内の特定のイベントのシーケンス。|51|いいえ|  
|EventSubClass|**int**|イベント サブクラスの種類。 再コンパイルの理由を示します。<br /><br /> 1 = スキーマの変更<br /><br /> 2 = 統計の変更<br /><br /> 3 = DNR による再コンパイル<br /><br /> 4 = 設定オプションの変更<br /><br /> 5 = 一時テーブルの変更<br /><br /> 6 = リモート行セットの変更<br /><br /> 7 = ブラウズ権限の変更<br /><br /> 8 = クエリ通知環境の変更<br /><br /> 9 = MPI ビューの変更<br /><br /> 10 = カーソル オプションの変更<br /><br /> 11 = 再コンパイル オプションあり|21|[ユーザー アカウント制御]|  
|GroupID|**int**|SQL トレース イベントが発生したワークロード グループの ID。|66|[ユーザー アカウント制御]|  
|HostName|**nvarchar**|クライアントが実行されているコンピューターの名前。 このデータ列にはクライアントからホスト名が提供されている場合に値が格納されます。 ホスト名を指定するには、HOST_NAME 関数を使用します。|8|[ユーザー アカウント制御]|  
|IntegerData2|**int**|再コンパイルの原因となったストアド プロシージャまたはバッチ内のステートメントの終了オフセット。 ステートメントがそのバッチの最後のステートメントである場合、終了オフセットは -1 です。|55|[ユーザー アカウント制御]|  
|IsSystem|**int**|イベントがシステム プロセスとユーザー プロセスのどちらで発生したか。 1 はシステム、0 はユーザーです。|60|[ユーザー アカウント制御]|  
|LoginName|**nvarchar**|ユーザーのログイン名 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セキュリティ ログインまたは DOMAIN\username という形式の [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ログイン資格情報)。|11|[ユーザー アカウント制御]|  
|LoginSid|**image**|ログイン ユーザーのセキュリティ ID 番号 (SID)。 この情報は、sys.server_principals カタログ ビューで参照できます。 各 SID はサーバーのログインごとに一意です。|41|[ユーザー アカウント制御]|  
|NestLevel|**int**|ストアド プロシージャの入れ子のレベル。|29|[ユーザー アカウント制御]|  
|NTDomainName|**nvarchar**|ユーザーが所属する Windows ドメイン。|7|[ユーザー アカウント制御]|  
|NTUserName|**nvarchar**|Windows のユーザー名。|6|[ユーザー アカウント制御]|  
|ObjectID|**int**|ストアド プロシージャにシステムが割り当てた ID。|22|[ユーザー アカウント制御]|  
|ObjectName|**nvarchar**|再コンパイルを発生させたオブジェクトの名前。|34|[ユーザー アカウント制御]|  
|ObjectType|**int**|イベントに関係するオブジェクトの種類を表す値。 詳細については、「 [ObjectType トレース イベント列](../../relational-databases/event-classes/objecttype-trace-event-column.md)」を参照してください。|28|[ユーザー アカウント制御]|  
|Offset|**int**|再コンパイルの原因となったストアド プロシージャまたはバッチ内のステートメントの開始オフセット。|61|[ユーザー アカウント制御]|  
|RequestID|**int**|ステートメントが含まれている要求の ID。|49|[ユーザー アカウント制御]|  
|ServerName|**nvarchar**|トレースされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの名前。|26|いいえ|  
|SessionLoginName|**nvarchar**|セッションを開始したユーザーのログイン名。 たとえば、Login1 を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、Login2 でステートメントを実行すると、SessionLoginName には Login1 が表示され、LoginName には Login2 が表示されます。 この列には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインと Windows ログインの両方が表示されます。|64|[ユーザー アカウント制御]|  
|SPID|**int**|イベントが発生したセッションの ID。|12|[ユーザー アカウント制御]|  
|SqlHandle|**varbinary**|64 ビット ハッシュ。アドホック クエリやデータベースのテキスト、および SQL オブジェクトのオブジェクト ID に基づいています。 この値を sys.dm_exec_sql_text に渡して、関連付けられている SQL テキストを取得できます。|63|[ユーザー アカウント制御]|  
|StartTime|**datetime**|イベントの開始時刻 (取得できた場合)。|14|[ユーザー アカウント制御]|  
|TextData|**ntext**|ステートメントレベルの再コンパイルの原因となった Transact-SQL ステートメントのテキスト。|1|[ユーザー アカウント制御]|  
|TransactionID|**bigint**|システムによって割り当てられたトランザクション ID。|4|[ユーザー アカウント制御]|  
|XactSequence|**bigint**|現在のトランザクションを説明するトークン。|50|[ユーザー アカウント制御]|  
  
## <a name="see-also"></a>参照  
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [SQL:StmtRecompile イベント クラス](../../relational-databases/event-classes/sql-stmtrecompile-event-class.md)  
  
  
