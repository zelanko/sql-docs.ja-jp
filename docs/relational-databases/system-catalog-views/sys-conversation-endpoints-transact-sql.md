---
title: sys.conversation_endpoints (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- conversation_endpoints_TSQL
- conversation_endpoints
- sys.conversation_endpoints
- sys.conversation_endpoints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.conversation_endpoints catalog view
ms.assetid: 2ed758bc-2a9d-4831-8da2-4b80e218f3ea
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 493fd7d0ce579073228c467226cef7ea86b2dc26
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47832130"
---
# <a name="sysconversationendpoints-transact-sql"></a>sys.conversation_endpoints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  各側、[!INCLUDE[ssSB](../../includes/sssb-md.md)]メッセージ交換はメッセージ交換のエンドポイントで表されます。 このカタログ ビューには、データベース内にあるメッセージ交換のエンドポイントごとに、1 行のデータが示されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|conversation_handle|**uniqueidentifier**|メッセージ交換のエンドポイントの識別子。 Null を許容しません。|  
|conversation_id|**uniqueidentifier**|メッセージ交換の識別子。 この識別子はメッセージ交換の両側で共有されます。 この識別子と is_initiator 列はデータベース内で一意です。 Null を許容しません。|  
|is_initiator|**tinyint**|エンドポイントが、メッセージ交換の発信側であるか、発信先であるかを示します。  Null を許容しません。<br /><br /> 1 = 発信側<br /><br /> 0 = 発信先|  
|service_contract_id|**int**|メッセージ交換のコントラクトの識別子。 Null を許容しません。|  
|conversation_group_id|**uniqueidentifier**|メッセージが属するメッセージ交換グループの識別子。 Null を許容しません。|  
|service_id|**int**|メッセージ交換の一方 (このビューを現在使用している側) で使用するサービスの識別子。 Null を許容しません。|  
|lifetime|**datetime**|メッセージ交換の有効期限 (日付と時刻)。 Null を許容しません。|  
|state|**char(2)**|メッセージ交換の現在の状態。 Null を許容しません。 次のいずれかです。<br /><br /> したがって送信開始。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] このメッセージ交換に対して BEGIN CONVERSATION が処理されたが、メッセージがまだ送信されていません。<br /><br /> SI 受信開始。 別のインスタンスで新しいメッセージ交換を開始する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]がまだ完全に受信の最初のメッセージ。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 最初のメッセージが受け取られなかった場合は、メッセージ交換をこの状態で作成可能性がありますまたは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]順序どおりにメッセージを受信します。 ただし、メッセージ交換で受信された最初の転送データに最初のメッセージ全体が含まれている場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で CO (メッセージ交換確立) 状態のメッセージ交換が作成されることがあります。<br /><br /> CO 会話しています。 メッセージ交換が確立され、メッセージ交換の両側でメッセージを送信できます。 通常のサービスでのメッセージ交換の大半は、メッセージ交換がこの状態のときに行われます。<br /><br /> DI 切断受信します。 メッセージ交換のリモート側で END CONVERSATION が発行されました。 メッセージ交換のローカル側で END CONVERSATION が発行されるまで、メッセージ交換はこの状態になります。 アプリケーションは、メッセージ交換のメッセージを受信も可能性があります。 メッセージ交換のリモート側ではメッセージ交換が終了しているので、このメッセージ交換でアプリケーションからメッセージを送信することはできません。 アプリケーションで END CONVERSATION を発行すると、メッセージ交換は CD (終了) 状態に移行します。<br /><br /> DO 送信切断。 メッセージ交換のローカル側で END CONVERSATION が発行されました。 メッセージ交換のリモート側で END CONVERSATION が承認されるまで、メッセージ交換はこの状態になります。 アプリケーションはこのメッセージ交換でメッセージを送受信することはできません。 メッセージ交換のリモート側で END CONVERSATION が承認されると、メッセージの交換は CD (終了) 状態に移行します。<br /><br /> ER エラーです。 このエンドポイントでエラーが発生しました。 エラー メッセージが、アプリケーション キューに配置されます。 アプリケーション キューが空白の場合、これはアプリケーションが既にエラー メッセージを受信したことを示します。<br /><br /> CD が閉じられます。 メッセージ交換のエンドポイントは解放されました。|  
|state_desc|**nvarchar(60)**|メッセージ交換のエンドポイントの状態の説明です。 このコラムでは、null 値です。 次のいずれかです。<br /><br /> **STARTED_OUTBOUND**<br /><br /> **STARTED_INBOUND**<br /><br /> **会話しています。**<br /><br /> **DISCONNECTED_INBOUND**<br /><br /> **DISCONNECTED_OUTBOUND**<br /><br /> **CLOSED**<br /><br /> **ERROR**|  
|far_service|**nvarchar (256)**|メッセージ交換のリモート側で使用されるサービスの名前。 Null を許容しません。|  
|far_broker_instance|**nvarchar(128)**|メッセージ交換のリモート側で使用されるブローカー インスタンス。 NULL 値は許可されます。|  
|principal_id|**int**|ダイアログのローカル側で使用される証明書を所有するプリンシパルの識別子。 Null を許容しません。|  
|far_principal_id|**int**|ダイアログのリモート側で使用される証明書を所有するユーザーの識別子。 Null を許容しません。|  
|outbound_session_key_identifier|**uniqueidentifier**|ダイアログで使用される送信暗号化キーの識別子。 Null を許容しません。|  
|inbound_session_key_identifier|**uniqueidentifier**|ダイアログで使用される受信暗号化キーの識別子。 Null を許容しません。|  
|security_timestamp|**datetime**|ローカルのセッション キーが作成された時刻。 Null を許容しません。|  
|dialog_timer|**datetime**|ダイアログで使用されるメッセージ交換タイマーによって DialogTimer メッセージが送信された時刻。 Null を許容しません。|  
|send_sequence|**bigint**|送信シーケンスの次のメッセージ番号。 Null を許容しません。|  
|last_send_tran_id|**binary(6)**|メッセージを送信する最後のトランザクションの内部トランザクション ID。 Null を許容しません。|  
|end_dialog_sequence|**bigint**|終了ダイアログ メッセージのシーケンス番号。 Null を許容しません。|  
|receive_sequence|**bigint**|メッセージ受信シーケンスで予測される次のメッセージ番号。 Null を許容しません。|  
|receive_sequence_frag|**int**|メッセージ受信シーケンスで予測される次のメッセージ フラグメント番号。 Null を許容しません。|  
|system_sequence|**bigint**|ダイアログの最後のシステム メッセージのシーケンス番号。 Null を許容しません。|  
|first_out_of_order_sequence|**bigint**|ダイアログの、順序どおりでないメッセージのうち最初のメッセージのシーケンス番号。 Null を許容しません。|  
|last_out_of_order_sequence|**bigint**|ダイアログの、順序どおりでないメッセージのうち最後のメッセージのシーケンス番号。 Null を許容しません。|  
|last_out_of_order_frag|**int**|ダイアログの、順序どおりでないメッセージ フラグメントのうち最後のメッセージのシーケンス番号。 Null を許容しません。|  
|is_system|**bit**|システム ダイアログの場合は 1。 Null を許容しません。|  
|priority|**tinyint**|このメッセージ交換のエンドポイントに割り当てられているメッセージ交換の優先度。 Null を許容しません。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
  
