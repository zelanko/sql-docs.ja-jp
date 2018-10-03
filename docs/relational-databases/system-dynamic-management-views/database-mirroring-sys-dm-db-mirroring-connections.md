---
title: sys.dm_db_mirroring_connections (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_db_mirroring_connections
- dm_db_mirroring_connections
- sys.dm_db_mirroring_connections_TSQL
- dm_db_mirroring_connections_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_mirroring_connections dynamic management view
ms.assetid: e4df91b6-0240-45d0-ae22-cb2c0d52e0b3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 624e3d8cd6bd92d07bf655e29060ed8809922cc2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47815360"
---
# <a name="database-mirroring---sysdmdbmirroringconnections"></a>データベース ミラーリング - sys.dm_db_mirroring_connections
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベース ミラーリング用に確立された接続ごとに 1 行を返します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**connection_id**|**uniqueidentifier**|接続の識別子。|  
|**transport_stream_id**|**uniqueidentifier**|識別子、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] TCP/IP 通信にこの接続で使用されるネットワーク インターフェイス (SNI) 接続します。|  
|**state**|**smallint**|接続の現在の状態。 有効値は次のとおりです。<br /><br /> 1 = NEW<br /><br /> 2 = CONNECTING<br /><br /> 3 = CONNECTED<br /><br /> 4 = LOGGED_IN<br /><br /> 5 = 終了|  
|**state_desc**|**nvarchar(60)**|接続の現在の状態。 有効値は次のとおりです。<br /><br /> NEW<br /><br /> CONNECTING<br /><br /> CONNECTED<br /><br /> LOGGED_IN<br /><br /> CLOSED|  
|**connect_time**|**datetime**|接続が開いた日付と時刻。|  
|**login_time**|**datetime**|接続のログインが成功した日付と時刻。|  
|**authentication_method**|**nvarchar(128)**|NTLM または KERBEROS など、Windows 認証方法の名前。 値は Windows から取得されます。|  
|**principal_name**|**nvarchar(128)**|接続権限が検証されたログインの名前。 Windows 認証の場合、この値はリモート ユーザー名になります。 証明書認証の場合、この値は証明書の所有者になります。|  
|**remote_user_name**|**nvarchar(128)**|Windows 認証で使用される他のデータベースのピア ユーザーの名前。|  
|**last_activity_time**|**datetime**|情報の送受信に接続が使用された最後の日付と時刻。|  
|**is_accept**|**bit**|接続がリモート側で生成されたかどうかを示します。<br /><br /> 1 = リモート インスタンスで受け入れられた要求の接続。<br /><br /> 0 = ローカル インスタンスで開始された接続。|  
|**login_state**|**smallint**|接続のログイン プロセスの状態。 次の値になります。<br /><br /> 0 = INITIAL<br /><br /> 1 = WAIT LOGIN NEGOTIATE<br /><br /> 2 = ONE ISC<br /><br /> 3 = ONE ASC<br /><br /> 4 = TWO ISC<br /><br /> 5 = TWO ASC<br /><br /> 6 = WAIT ISC Confirm<br /><br /> 7 = WAIT ASC Confirm<br /><br /> 8 = WAIT REJECT<br /><br /> 9 = WAIT PRE-MASTER SECRET<br /><br /> 10 = WAIT VALIDATION<br /><br /> 11 = WAIT ARBITRATION<br /><br /> 12 = オンライン<br /><br /> 13 = ERROR|  
|**login_state_desc**|**nvarchar(60)**|リモート コンピューターからのログインに関する現在の状態。 有効値は次のとおりです。<br /><br /> 接続ハンドシェイクを初期化しています。<br /><br /> 接続ハンドシェイクは、Login Negotiate メッセージを待機しています。<br /><br /> 接続ハンドシェイクを初期化し、認証用のセキュリティ コンテキストを送信しました。<br /><br /> 接続ハンドシェイクを受信し、認証用のセキュリティ コンテキストを承諾しました。<br /><br /> 接続ハンドシェイクを初期化し、認証用のセキュリティ コンテキストを送信しました。 ピアを認証するために使用できるオプションのメカニズムがあります。<br /><br /> 接続ハンドシェイクを受信し、認証用のセキュリティ コンテキストを送信しました。 ピアを認証するために使用できるオプションのメカニズムがあります。<br /><br /> 接続ハンドシェイクは、Initialize Security Context Confirmation メッセージを待機しています。<br /><br /> 接続ハンドシェイクは、Accept Security Context Confirmation メッセージを待機しています。<br /><br /> 接続ハンドシェイクは、失敗した認証に関する SSPI 拒否メッセージを待機しています。<br /><br /> 接続ハンドシェイクは、Pre-Master Secret メッセージを待機しています。<br /><br /> 接続ハンドシェイクは、Validation メッセージを待機しています。<br /><br /> 接続ハンドシェイクは、Arbitration メッセージを待機しています。<br /><br /> 接続ハンドシェイクが完了し、メッセージ交換がオンラインになりました (準備ができました)。<br /><br /> 接続にエラーがあります。|  
|**peer_certificate_id**|**int**|認証用のリモート インスタンスで使用する証明書のローカルのオブジェクト ID。 この証明書の所有者には、データベース ミラーリング エンドポイントへの CONNECT 権限が必要です。|  
|**encryption_algorithm**|**smallint**|接続で使用される暗号化アルゴリズム。 NULL 値は許可されます。 有効値は次のとおりです。<br /><br /> **値:** 0<br /><br /> **説明:** なし<br /><br /> **DDL オプション:** 無効になっています。<br /><br /> **値:** 1<br /><br /> **説明:** RC4<br /><br /> **DDL オプション:** {0} に必要な&#124;アルゴリズム RC4 が必要}<br /><br /> **値:** 2<br /><br /> **説明:** AES<br /><br /> **DDL オプション:** アルゴリズム AES が必要<br /><br /> **値:** 3<br /><br /> **説明:** None、RC4<br /><br /> **DDL オプション:** {0} サポートされている&#124;サポートされているアルゴリズム RC4}<br /><br /> **値:** 4<br /><br /> **説明:** none、AES<br /><br /> **DDL オプション:** サポートされているアルゴリズム RC4<br /><br /> **値:** 5<br /><br /> **説明:** RC4、AES<br /><br /> **DDL オプション:** アルゴリズム RC4 AES が必要<br /><br /> **値:** 6<br /><br /> **説明:** AES、RC4<br /><br /> **DDL オプション:** アルゴリズム AES RC4 が必要<br /><br /> **値:** 7<br /><br /> **説明:** NONE、RC4、AES<br /><br /> **DDL オプション:** サポート アルゴリズム RC4 AES<br /><br /> **値:** 8<br /><br /> **説明:** NONE、AES、RC4<br /><br /> **DDL オプション:** アルゴリズム AES RC4 をサポートされています。<br /><br /> **注:** RC4 アルゴリズムは旧バージョンとの互換性のためのみサポートされます。 データベース互換性レベルが 90 または 100 の場合、新しい素材は RC4 または RC4_128 を使用してのみ暗号化できます  (非推奨)。AES アルゴリズムのいずれかなど、新しいアルゴリズムを使用してください。 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]でき、以降のバージョンでは、RC4 または RC4_128 を使用して暗号化された素材を復号化されたどの互換性レベル。|  
|**encryption_algorithm_desc**|**nvarchar(60)**|暗号化アルゴリズムのテキスト表示。 NULL 値は許可されます。 有効値は次のとおりです。<br /><br /> **説明:** なし<br /><br /> **DDL オプション:** 無効になっています。<br /><br /> **説明:** RC4<br /><br /> **DDL オプション:** {0} に必要な&#124;アルゴリズム RC4 が必要}<br /><br /> **説明:** AES<br /><br /> **DDL オプション:** アルゴリズム AES が必要<br /><br /> **説明:** NONE、RC4<br /><br /> **DDL オプション:** {サポート&#124;アルゴリズム RC4 をサポート}<br /><br /> **説明:** NONE、AES<br /><br /> **DDL オプション:** アルゴリズム RC4 をサポート<br /><br /> **説明:** RC4、AES<br /><br /> **DDL オプション:** のために必要なアルゴリズム RC4 AES<br /><br /> **説明:** AES、RC4<br /><br /> **DDL オプション:** アルゴリズム AES RC4 が必要<br /><br /> **説明:** NONE、RC4、AES<br /><br /> **DDL オプション:** サポート アルゴリズム RC4 AES<br /><br /> **説明:** NONE、AES、RC4<br /><br /> **DDL オプション:** アルゴリズム AES RC4 をサポート|  
|**receives_posted**|**smallint**|この接続でまだ完了していない非同期ネットワーク受信の数。|  
|**is_receive_flow_controlled**|**bit**|ネットワークがビジー状態のときに行われたフロー制御が原因で、ネットワーク受信が延期されたかどうか。<br /><br /> 1 = True|  
|**sends_posted**|**smallint**|この接続でまだ完了していない非同期ネットワーク送信の数。|  
|**is_send_flow_controlled**|**bit**|ネットワークがビジー状態のときに行われたフロー制御が原因で、ネットワーク送信が延期されたかどうか。<br /><br /> 1 = True|  
|**total_bytes_sent**|**bigint**|この接続で送信された合計バイト数。|  
|**total_bytes_received**|**bigint**|この接続で受信したバイト数の合計数。|  
|**total_fragments_sent**|**bigint**|この接続で送信されたデータベース ミラーリング メッセージ フラグメントの合計数。|  
|**total_fragments_received**|**bigint**|この接続で受信されたデータベース ミラーリング メッセージ フラグメントの合計数。|  
|**total_sends**|**bigint**|ネットワークの合計数は、この接続で発行された要求を送信します。|  
|**total_receives**|**bigint**|ネットワークの合計数は、この接続で発行された要求を受信します。|  
|**peer_arbitration_id**|**uniqueidentifier**|エンドポイントの内部識別子。 NULL 値は許可されます。|  
  
## <a name="permissions"></a>アクセス許可  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="physical-joins"></a>物理結合  
 ![sys.join_dm_db_mirroring_connections の結合](../../relational-databases/system-dynamic-management-views/media/join-dm-db-mirroring-connections.gif "sys.join_dm_db_mirroring_connections の結合")  
  
## <a name="relationship-cardinalities"></a>リレーションシップの基数  
  
|From|変換先|リレーションシップ|  
|----------|--------|------------------|  
|**dm_db_mirroring_connections.connection_id**|**dm_exec_connections.connection_id**|一対一|  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [データベース ミラーリングの監視 &#40;SQL Server&#41;](../../database-engine/database-mirroring/monitoring-database-mirroring-sql-server.md)  
  
  
