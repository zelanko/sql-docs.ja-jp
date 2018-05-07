---
title: sys.dm_broker_connections (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/08/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_broker_connections
- dm_broker_connections
- sys.dm_broker_connections_TSQL
- dm_broker_connections_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_broker_connections dynamic management view
ms.assetid: d9e20433-67fe-4fcc-80e3-b94335b2daef
caps.latest.revision: 45
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 93a7aa9c1bb26b8041a2a6a5a3ff0b394ceb2ad6
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sysdmbrokerconnections-transact-sql"></a>sys.dm_broker_connections (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  行をそれぞれ返します[!INCLUDE[ssSB](../../includes/sssb-md.md)]ネットワーク接続します。 次の表は、詳細を示します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**connection_id**|**uniqueidentifier**|接続の識別子。 NULL 値は許可されます。|  
|**transport_stream_id**|**uniqueidentifier**|識別子、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] TCP/IP 通信にこの接続で使用されるネットワーク インターフェイス (SNI) 接続します。 NULL 値は許可されます。|  
|**状態**|**smallint**|接続の現在の状態。 NULL 値は許可されます。 有効値は次のとおりです。<br /><br /> 1 = NEW<br /><br /> 2 = CONNECTING<br /><br /> 3 = CONNECTED<br /><br /> 4 = LOGGED_IN<br /><br /> 5 = 終了|  
|**state_desc**|**nvarchar(60)**|接続の現在の状態。 NULL 値は許可されます。 有効値は次のとおりです。<br /><br /> NEW<br /><br /> CONNECTING<br /><br /> CONNECTED<br /><br /> LOGGED_IN<br /><br /> CLOSED|  
|**connect_time**|**datetime**|接続が開いた日付と時刻。 NULL 値は許可されます。|  
|**login_time**|**datetime**|接続のログインが成功した日付と時刻。 NULL 値は許可されます。|  
|**authentication_method**|**nvarchar(128)**|NTLM または KERBEROS など、Windows 認証方法の名前。 値は Windows から取得されます。 NULL 値は許可されます。|  
|**principal_name**|**nvarchar(128)**|接続権限が検証されたログインの名前。 Windows 認証の場合、この値はリモート ユーザー名になります。 証明書認証の場合、この値は証明書の所有者になります。 NULL 値は許可されます。|  
|**remote_user_name**|**nvarchar(128)**|Windows 認証で使用される他のデータベースのピア ユーザーの名前。 NULL 値は許可されます。|  
|**last_activity_time**|**datetime**|情報の送受信に接続が使用された最後の日付と時刻。 NULL 値は許可されます。|  
|**is_accept**|**bit**|接続がリモート側で生成されたかどうかを示します。 NULL 値は許可されます。<br /><br /> 1 = リモート インスタンスで受け入れられた要求の接続。<br /><br /> 0 = ローカル インスタンスで開始された接続。|  
|**login_state**|**smallint**|接続のログイン プロセスの状態。 次の値になります。<br /><br /> 0 = INITIAL<br /><br /> 1 = WAIT LOGIN NEGOTIATE<br /><br /> 2 = ONE ISC<br /><br /> 3 = ONE ASC<br /><br /> 4 = TWO ISC<br /><br /> 5 = TWO ASC<br /><br /> 6 = WAIT ISC Confirm<br /><br /> 7 = WAIT ASC Confirm<br /><br /> 8 = WAIT REJECT<br /><br /> 9 = WAIT PRE-MASTER SECRET<br /><br /> 10 = WAIT VALIDATION<br /><br /> 11 = WAIT ARBITRATION<br /><br /> 12 = オンライン<br /><br /> 13 = ERROR|  
|**login_state_desc**|**nvarchar(60)**|リモート コンピューターからのログインに関する現在の状態。 有効値は次のとおりです。<br /><br /> 接続ハンドシェイクを初期化しています。<br /><br /> 接続ハンドシェイクは、Login Negotiate メッセージを待機しています。<br /><br /> 接続ハンドシェイクを初期化し、認証用のセキュリティ コンテキストを送信しました。<br /><br /> 接続ハンドシェイクを受信し、認証用のセキュリティ コンテキストを承諾しました。<br /><br /> 接続ハンドシェイクを初期化し、認証用のセキュリティ コンテキストを送信しました。 ピアを認証するために使用できるオプションのメカニズムがあります。<br /><br /> 接続ハンドシェイクを受信し、認証用のセキュリティ コンテキストを送信しました。 ピアを認証するために使用できるオプションのメカニズムがあります。<br /><br /> 接続ハンドシェイクは、Initialize Security Context Confirmation メッセージを待機しています。<br /><br /> 接続ハンドシェイクは、Accept Security Context Confirmation メッセージを待機しています。<br /><br /> 接続ハンドシェイクは、失敗した認証に関する SSPI 拒否メッセージを待機しています。<br /><br /> 接続ハンドシェイクは、Pre-Master Secret メッセージを待機しています。<br /><br /> 接続ハンドシェイクは、Validation メッセージを待機しています。<br /><br /> 接続ハンドシェイクは、Arbitration メッセージを待機しています。<br /><br /> 接続ハンドシェイクが完了し、メッセージ交換がオンラインになりました (準備ができました)。<br /><br /> 接続にエラーがあります。|  
|**peer_certificate_id**|**int**|認証でリモート インスタンスによって使用される証明書のローカル オブジェクト ID。 この証明書の所有者への CONNECT 権限を持つ必要があります、[!INCLUDE[ssSB](../../includes/sssb-md.md)]エンドポイント。 NULL 値は許可されます。|  
|**encryption_algorithm**|**smallint**|接続で使用される暗号化アルゴリズム。 NULL 値は許可されます。 有効値は次のとおりです。<br /><br /> **値&#124;説明&#124;対応する DDL オプション**<br /><br /> 0 &#124; none&#124;無効になっています。<br /><br /> 1&AMP;#124;署名のみ<br /><br /> 2 &#124; AES、RC4&#124;必要&#124;アルゴリズム RC4 が必要}<br /><br /> 3 &#124; AES&#124;アルゴリズム AES が必要<br /><br /> **注:** RC4 アルゴリズムは、旧バージョンとの互換性に対してのみサポートされます。 データベース互換性レベルが 90 または 100 の場合、新しい素材は RC4 または RC4_128 を使用してのみ暗号化できます  (非推奨)。AES アルゴリズムのいずれかなど、新しいアルゴリズムを使用してください。 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以降のバージョンでは、どの互換性レベルでも、RC4 または RC4_128 を使用して暗号化された素材を暗号化解除できます。|  
|**encryption_algorithm_desc**|**nvarchar(60)**|暗号化アルゴリズムのテキスト表示。 NULL 値は許可されます。 有効値は次のとおりです。<br /><br /> **説明&#124;対応する DDL オプション**<br /><br /> NONE&#124;無効になっています。<br /><br /> RC4 &#124; {必要&#124;アルゴリズム RC4 が必要}<br /><br /> AES&#124;アルゴリズム AES が必要<br /><br /> NONE、RC4 &#124; {サポート&#124;アルゴリズム RC4 をサポート}<br /><br /> NONE、AES&#124;アルゴリズム RC4 をサポート<br /><br /> RC4、AES&#124;必要アルゴリズム RC4 AES<br /><br /> AES、RC4&#124;アルゴリズム AES RC4 が必要<br /><br /> NONE、RC4、AES&#124;アルゴリズム RC4 をサポートされている AES<br /><br /> NONE、AES、RC4&#124;アルゴリズム AES RC4 をサポート|  
|**receives_posted**|**smallint**|この接続でまだ完了していない非同期ネットワーク受信の数。 NULL 値は許可されます。|  
|**is_receive_flow_controlled**|**bit**|ネットワークがビジー状態のときに行われたフロー制御が原因で、ネットワーク受信が延期されたかどうか。 NULL 値は許可されます。<br /><br /> 1 = True|  
|**sends_posted**|**smallint**|この接続でまだ完了していない非同期ネットワーク送信の数。 NULL 値は許可されます。|  
|**is_send_flow_controlled**|**bit**|ネットワークがビジー状態のときに行われたフロー制御が原因で、ネットワーク送信が延期されたかどうか。 NULL 値は許可されます。<br /><br /> 1 = True|  
|**total_bytes_sent**|**bigint**|この接続で送信されたバイトの合計数。 NULL 値は許可されます。|  
|**total_bytes_received**|**bigint**|この接続で受信された合計バイト数。 NULL 値は許可されます。|  
|**total_fragments_sent**|**bigint**|この接続で送信された [!INCLUDE[ssSB](../../includes/sssb-md.md)] メッセージ フラグメントの合計数。 NULL 値は許可されます。|  
|**total_fragments_received**|**bigint**|この接続で受信された [!INCLUDE[ssSB](../../includes/sssb-md.md)] メッセージ フラグメントの合計数。 NULL 値は許可されます。|  
|**total_sends**|**bigint**|この接続で発行されたネットワーク送信要求の合計数。 NULL 値は許可されます。|  
|**total_receives**|**bigint**|この接続で発行されたネットワーク受信要求の合計数。 NULL 値は許可されます。|  
|**peer_arbitration_id**|**uniqueidentifier**|エンドポイントの内部識別子。 NULL 値は許可されます。|  
  
## <a name="permissions"></a>権限  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="physical-joins"></a>物理結合  
 ![Sys.dm_broker_connections の結合](../../relational-databases/system-dynamic-management-views/media/join-dm-broker-connections-1.gif "sys.dm_broker_connections の結合")  
  
## <a name="relationship-cardinalities"></a>リレーションシップの基数  
  
|From|変換先|リレーションシップ|  
|----------|--------|------------------|  
|**dm_broker_connections.connection_id**|**dm_exec_connections.connection_id**|一対一|  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Service Broker 関連の動的管理ビュー & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/service-broker-related-dynamic-management-views-transact-sql.md)  
  
  

