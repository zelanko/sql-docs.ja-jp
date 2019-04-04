---
title: sysmail_unsentitems (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_unsentitems_TSQL
- sysmail_unsentitems
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_unsentitems database mail view
ms.assetid: 993c12da-41e5-4e53-a188-0323feb70c67
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9de1f394184c6dab26f691251af85bfe631ae6c2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47724930"
---
# <a name="sysmailunsentitems-transact-sql"></a>sysmail_unsentitems (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベース メール メッセージを 1 つの行が含まれています、**未送信**または**再試行**状態。 状態が unsent または retrying のメッセージは、メール キューに残っており、いつでも送信される可能性があります。 メッセージを持つことができます、**未送信**理由は次の状態。  
  
-   メッセージが新しく、メール キューに挿入されていても、データベース メールが他のメッセージの処理中でこのメッセージに達していない。  
  
-   データベース メール外部プログラムが実行されておらず、メールが送信されていない  
  
 メッセージを持つことができます、**再試行**理由は次の状態。  
  
-   データベース メールでメッセージの送信が試行されたが、SMTP メール サーバーに接続できなかった。 この場合、データベース メールでは、メッセージを送信したプロファイルに割り当てられている他のデータベース メール アカウントを使用して、メッセージの送信が引き続き試行されます。 データベース メールが用に構成された時間の長さを待つ場合、アカウントは、メールを送信しない、**アカウントの再試行間隔**パラメーターとした後、もう一度メッセージを送信します。 データベース メールでは、**アカウントの再試行回数**メッセージを送信しようとする回数を決定するパラメーター。 メッセージの保持**再試行**データベース メールがメッセージを送信しようとならない限り状態。  
  
 このビューは、送信待ちメッセージの数と、それらのメール キューでの待機時間を確認する場合に使用できます。 通常の数**未送信**メッセージは低くなります。 通常の運用中にベンチマーク テストを行って、その運用に適切な、メッセージ キュー内のメッセージの数を判断してください。  
  
 データベース メールで処理されたすべてのメッセージを表示する[sysmail_allitems &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-allitems-transact-sql.md)します。 状態が失敗したメッセージのみを表示する[sysmail_faileditems &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-faileditems-transact-sql.md)します。 送信されたメッセージのみを表示する[sysmail_sentitems &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-sentitems-transact-sql.md)します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**mailitem_id**|**int**|メール キュー内のメール アイテムの識別子。|  
|**profile_id**|**int**|メッセージの送信に使用されたプロファイルの識別子。|  
|**recipients**|**varchar(max)**|メッセージ受信者の電子メール アドレス。|  
|**copy_recipients**|**varchar(max)**|CC としてメッセージのコピーを受け取る受信者の電子メール アドレス。|  
|**blind_copy_recipients**|**varchar(max)**|BCC としてメッセージのコピーを受け取る受信者の電子メール アドレス。この受信者の名前は、メッセージ ヘッダーには表示されません。|  
|**subject**|**nvarchar(510)**|メッセージの件名。|  
|**body**|**varchar(max)**|メッセージの本文。|  
|**body_format**|**varchar(20)**|メッセージの本文の書式。 指定できる値は**テキスト**と**HTML**します。|  
|**importance**|**varchar(6)**|**重要度**メッセージのパラメーター。|  
|**sensitivity**|**varchar(12)**|**感度**メッセージのパラメーター。|  
|**file_attachments**|**varchar(max)**|電子メール メッセージに添付されたファイル名の、セミコロン区切りの一覧。|  
|**attachment_encoding**|**varchar(20)**|添付ファイルの種類。|  
|**query**|**varchar(max)**|メール プログラムによって実行されたクエリ。|  
|**execute_query_database**|**sysname**|メール プログラムによってクエリが実行されたデータベース コンテキスト。|  
|**attach_query_result_as_file**|**bit**|値が 0 の場合、クエリの結果が電子メール メッセージ本文内に取り込まれ、本文内容の後に追加されていることを示します。 値が 1 の場合、結果が添付ファイルとして返されたことを示します。|  
|**query_result_header**|**bit**|値が 1 の場合、クエリの結果に列のヘッダーが含まれていることを示します。 値が 0 の場合、クエリの結果に列のヘッダーが含まれていないことを示します。|  
|**query_result_width**|**int**|**Query_result_width**メッセージのパラメーター。|  
|**query_result_separator**|**char(1)**|クエリの出力で列の区切りに使用された文字。|  
|**exclude_query_output**|**bit**|**Exclude_query_output**メッセージのパラメーター。 詳細については、[sp_send_dbmail &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-send-dbmail-transact-sql.md)を参照してください。|  
|**append_query_error**|**bit**|**Append_query_error**メッセージのパラメーター。 0 は、クエリにエラーがあった場合、データベース メールで電子メール メッセージが送信されないことを示します。|  
|**send_request_date**|**datetime**|メッセージがメール キューに挿入された日時。|  
|**send_request_user**|**sysname**|メッセージを送信したユーザー。 データベース メール プロシージャのユーザー コンテキストでない、**から**メッセージのフィールド。|  
|**sent_account_id**|**int**|メッセージの送信に使用されたデータベース メール アカウントの識別子。 このビューでは常に NULL になります。|  
|**sent_status**|**varchar(8)**|**未送信**データベース メール、メールの送信が試行されていない場合。 **再試行**メッセージを送信できませんでした。 データベース メールが再試行されている場合。|  
|**sent_date**|**datetime**|データベース メールでメールの送信が試行された日時。 データベース メールでメッセージの送信が試行されていない場合は NULL になります。|  
|**last_mod_date**|**datetime**|行が最後に変更された日時。|  
|**last_mod_user**|**sysname**|行を最後に変更したユーザー。|  
  
## <a name="remarks"></a>コメント  
 データベース メールのトラブルシューティングを行うとき、このビューでは送信済みのメッセージ数とメッセージの待機時間を確認できるので、問題の性質を特定するのに役立ちます。 メッセージが 1 つも送信されていない場合は、データベース メール外部プログラムが動作していないか、ネットワークの問題によってデータベース メールから SMTP サーバーへの接続に障害が発生している可能性があります。 未送信のメッセージの多くが同じ**profile_id**、SMTP サーバーで問題がある可能性があります。 この場合は、プロファイルへのアカウントの追加を検討してください。 場合は、メッセージが送信されているが、メッセージがキューで多くの時間を費やしている[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]より多くのリソースが必要なメッセージの量を処理する必要があります。  
  
## <a name="permissions"></a>アクセス許可  
 与えられる**sysadmin**固定サーバー ロールと**DatabaseMailUserRole**データベース ロール。 メンバーによって実行されると、 **sysadmin**固定サーバー ロールに、このビューにはすべて**未送信**または**再試行**メッセージ。 その他のすべてのユーザーのみを表示、**未送信**または**再試行**自分が送信したメッセージ。  
  
  
