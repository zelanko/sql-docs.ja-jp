---
title: "sysmail_allitems (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysmail_allitems_TSQL
- sysmail_allitems
dev_langs: TSQL
helpviewer_keywords: sysmail_allitems database mail view
ms.assetid: 21fb8432-7677-4435-902f-64a58bba4cbb
caps.latest.revision: "17"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: ba8deb3b11b01cf9f53e02024815150fa4441b6d
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="sysmailallitems-transact-sql"></a>sysmail_allitems (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベース メールで処理されたメッセージごとに 1 行のデータを格納します。 このビューは、すべてのメッセージの状態を確認するときに使用できます。  
  
 状態が失敗したメッセージのみを表示する[sysmail_faileditems (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sysmail-faileditems-transact-sql.md). 未送信のメッセージだけを表示する[sysmail_unsentitems (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sysmail-unsentitems-transact-sql.md). 送信されたメッセージのみを表示する[sysmail_sentitems (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sysmail-sentitems-transact-sql.md).  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**mailitem_id**|**int**|メール キュー内のメール アイテムの識別子。|  
|**profile_id**|**int**|メッセージを送信するために使用するプロファイルの識別子。|  
|**受信者**|**varchar(max)**|メッセージ受信者の電子メール アドレス。|  
|**@copy_recipients**|**varchar(max)**|CC としてメッセージのコピーを受け取る受信者の電子メール アドレス。|  
|**@blind_copy_recipients**|**varchar(max)**|BCC としてメッセージのコピーを受け取る受信者の電子メール アドレス。この受信者の名前は、メッセージ ヘッダーには表示されません。|  
|**件名**|**nvarchar(510)**|メッセージの件名。|  
|**本文**|**varchar(max)**|メッセージの本文。|  
|**body_format**|**varchar (20)**|メッセージの本文の書式。 可能な値は TEXT と HTML です。|  
|**重要度**|**varchar (6)**|**重要度**メッセージのパラメーターです。|  
|**小文字の区別**|**varchar (12)**|**感度**メッセージのパラメーターです。|  
|**@file_attachments**|**varchar(max)**|電子メール メッセージに添付されたファイル名の、セミコロン区切りの一覧。|  
|**attachment_encoding**|**varchar (20)**|添付ファイルの種類。|  
|**クエリ**|**varchar(max)**|メール プログラムによって実行されたクエリ。|  
|**@execute_query_database**|**sysname**|メール プログラムによってクエリが実行されたデータベース コンテキスト。|  
|**attach_query_result_as_file**|**bit**|値が 0 の場合、クエリの結果が電子メール メッセージ本文内に取り込まれ、本文内容の後に追加されていることを示します。 値が 1 の場合、結果が添付ファイルとして返されたことを示します。|  
|**query_result_header**|**bit**|値が 1 の場合、クエリの結果に列のヘッダーが含まれていることを示します。 値が 0 の場合、クエリの結果に列のヘッダーが含まれていないことを示します。|  
|**query_result_width**|**int**|**Query_result_width**メッセージのパラメーターです。|  
|**@query_result_separator**|**char (1)**|クエリの出力で列の区切りに使用された文字。|  
|**exclude_query_output**|**bit**|**Exclude_query_output**メッセージのパラメーターです。 詳細については、次を参照してください。 [sp_send_dbmail &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-send-dbmail-transact-sql.md).|  
|**append_query_error**|**bit**|**Append_query_error**メッセージのパラメーターです。 0 は、クエリにエラーがあった場合、データベース メールで電子メール メッセージが送信されないことを示します。|  
|**send_request_date**|**datetime**|メッセージがメール キューに挿入された日時。|  
|**send_request_user**|**sysname**|メッセージを送信したユーザー。 これはメッセージの [差出人] フィールドに表示されるユーザーではなく、データベース メール プロシージャのユーザー コンテキストです。|  
|**sent_account_id**|**int**|メッセージの送信に使用されたデータベース メール アカウントの識別子。|  
|**sent_status**|**varchar (8)**|メールの状態。 有効な値は次のとおりです。<br /><br /> **送信**-メールが送信されました。<br /><br /> **未送信**-データベース メールがメッセージの送信を試みている最中です。<br /><br /> **再試行**-データベース メール メッセージの送信に失敗しましたが、再送信しようとしていますがします。<br /><br /> **失敗**-データベース メールがメッセージを送信できませんでした。|  
|**sent_date**|**datetime**|メッセージが送信された日時。|  
|**last_mod_date**|**datetime**|行が最後に変更された日時。|  
|**last_mod_user**|**sysname**|行を最後に変更したユーザー。|  
  
## <a name="remarks"></a>解説  
 使用して、 **sysmail_allitems**データベース メールで処理されるすべてのメッセージの状態を表示するビュー。 データベース メールのトラブルシューティングを行うとき、このビューでは送信済みとそれ以外のメッセージの属性を比較できるので、問題の性質を特定するのに役立ちます。  
  
 このビューによって公開されているシステム テーブルのすべてのメッセージを含むし、発生する可能性があります、 **msdb**データベースを拡張します。 古いメッセージをビューから定期的に削除して、テーブルのサイズを縮小するようにしてください。 詳細については、次を参照してください。[アーカイブ データベース メール メッセージおよびイベント ログには、SQL Server エージェント ジョブを作成する](../../relational-databases/database-mail/create-a-sql-server-agent-job-to-archive-database-mail-messages-and-event-logs.md)です。  
  
## <a name="permissions"></a>Permissions  
 付与された**sysadmin**固定サーバー ロールと**DatabaseMailUserRole**データベース ロール。 メンバーによって実行されると、 **sysadmin**固定サーバー ロールに、このビューはすべてのメッセージを表示します。 他のすべてのユーザーには、送信したメッセージのみを参照してください。  
  
  
