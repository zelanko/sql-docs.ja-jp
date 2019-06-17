---
title: sysmail_allitems (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_allitems_TSQL
- sysmail_allitems
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_allitems database mail view
ms.assetid: 21fb8432-7677-4435-902f-64a58bba4cbb
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 65c96ade0964146e1d8ff9cfa52f99938d290712
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62759860"
---
# <a name="sysmailallitems-transact-sql"></a>sysmail_allitems (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベース メールで処理されたメッセージごとに 1 行のデータを格納します。 このビューは、すべてのメッセージの状態を確認するときに使用できます。  
  
 状態が失敗したメッセージのみを表示する[sysmail_faileditems &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-faileditems-transact-sql.md)します。 未送信のメッセージだけを表示する[sysmail_unsentitems &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-unsentitems-transact-sql.md)します。 送信されたメッセージのみを表示する[sysmail_sentitems &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-sentitems-transact-sql.md)します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**mailitem_id**|**int**|メール キュー内のメール アイテムの識別子。|  
|**profile_id**|**int**|メッセージを送信するために使用するプロファイルの識別子。|  
|**recipients**|**varchar(max)**|メッセージ受信者の電子メール アドレス。|  
|**copy_recipients**|**varchar(max)**|CC としてメッセージのコピーを受け取る受信者の電子メール アドレス。|  
|**blind_copy_recipients**|**varchar(max)**|BCC としてメッセージのコピーを受け取る受信者の電子メール アドレス。この受信者の名前は、メッセージ ヘッダーには表示されません。|  
|**subject**|**nvarchar(510)**|メッセージの件名。|  
|**body**|**varchar(max)**|メッセージの本文。|  
|**body_format**|**varchar(20)**|メッセージの本文の書式。 可能な値は TEXT と HTML です。|  
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
|**exclude_query_output**|**bit**|**Exclude_query_output**メッセージのパラメーター。 詳細については、次を参照してください。 [sp_send_dbmail &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-send-dbmail-transact-sql.md)します。|  
|**append_query_error**|**bit**|**Append_query_error**メッセージのパラメーター。 0 は、クエリにエラーがあった場合、データベース メールで電子メール メッセージが送信されないことを示します。|  
|**send_request_date**|**datetime**|メッセージがメール キューに挿入された日時。|  
|**send_request_user**|**sysname**|メッセージを送信したユーザー。 これはメッセージの [差出人] フィールドに表示されるユーザーではなく、データベース メール プロシージャのユーザー コンテキストです。|  
|**sent_account_id**|**int**|メッセージの送信に使用されたデータベース メール アカウントの識別子。|  
|**sent_status**|**varchar(8)**|メールの状態。 有効な値は次のとおりです。<br /><br /> **送信**-メールが送信されました。<br /><br /> **未送信**-データベース メールがまだメッセージを送信しようとしています。<br /><br /> **再試行**-データベース メール メッセージの送信に失敗しましたが、もう一度送信しようとします。<br /><br /> **失敗**-データベース メールがメッセージを送信できませんでした。|  
|**sent_date**|**datetime**|メッセージが送信された日時。|  
|**last_mod_date**|**datetime**|行が最後に変更された日時。|  
|**last_mod_user**|**sysname**|行を最後に変更したユーザー。|  
  
## <a name="remarks"></a>コメント  
 使用して、 **sysmail_allitems**をすべてのメッセージの状態を表示するビューは、データベース メールで処理します。 データベース メールのトラブルシューティングを行うとき、このビューでは送信済みとそれ以外のメッセージの属性を比較できるので、問題の性質を特定するのに役立ちます。  
  
 このビューによって公開されているシステム テーブルのすべてのメッセージを含むし、可能性があります、 **msdb**データベースを拡張します。 古いメッセージをビューから定期的に削除して、テーブルのサイズを縮小するようにしてください。 詳細については、次を参照してください。[アーカイブ データベース メール メッセージやイベント ログには、SQL Server エージェント ジョブを作成する](../../relational-databases/database-mail/create-a-sql-server-agent-job-to-archive-database-mail-messages-and-event-logs.md)します。  
  
## <a name="permissions"></a>アクセス許可  
 与えられる**sysadmin**固定サーバー ロールと**DatabaseMailUserRole**データベース ロール。 メンバーによって実行されると、 **sysadmin**固定サーバー ロールに、このビューはすべてのメッセージを表示します。 その他のすべてのユーザーには、自分が送信したメッセージのみを参照してください。  
  
  
