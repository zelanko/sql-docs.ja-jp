---
title: sysmail_event_log (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysmail_event_log
- sysmail_event_log_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_event_log database mail view
ms.assetid: 440bc409-1188-4175-afc4-c68e31e44fed
caps.latest.revision: 16
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e2f9818bda47d9e0ffac256220f36efa1c5c6360
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sysmaileventlog-transact-sql"></a>sysmail_event_log (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベース メール システムから返される、Windows または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のメッセージごとに 1 行のデータを格納します。 ここでのメッセージとは、電子メール メッセージではなくエラー メッセージなどのメッセージを指します。構成、**ログ記録レベル**パラメーターを使用して、**システム パラメーターの構成**、データベース メール構成ウィザードのダイアログ ボックスまたは[sysmail_configure_sp](../../relational-databases/system-stored-procedures/sysmail-configure-sp-transact-sql.md)ストアド プロシージャをどのメッセージを返すかを判断します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**Log_id**|**int**|ログ内のアイテムの識別子。|  
|**event_type**|**varchar(11)**|ログに挿入された通知の種類。 可能な値は、エラー、警告、情報メッセージ、成功メッセージ、およびその他の内部メッセージです。|  
|**log_date**|**datetime**|ログ エントリが作成された日時。|  
|**説明**|**nvarchar(max)**|記録されたメッセージのテキスト。|  
|**process_id**|**int**|データベース メール外部プログラムのプロセス ID。 通常、データベース メール外部プログラムが起動するたびに変更されます。|  
|**mailitem_id**|**int**|メール キュー内のメール アイテムの識別子。 メッセージが特定の電子メール アイテムに関係していない場合は NULL になります。|  
|**account_id**|**int**|**Account_id**のイベントに関連するアカウント。 メッセージが特定のアカウントに関係していない場合は NULL になります。|  
|**last_mod_date**|**datetime**|行が最後に変更された日時。|  
|**last_mod_user**|**sysname**|行を最後に変更したユーザー。 電子メールの場合は、メールを送信したユーザーになります。 データベース メール外部プログラムにより生成されたメッセージの場合は、プログラムのユーザー コンテキストになります。|  
  
## <a name="remarks"></a>解説  
 データベース メールのトラブルシューティングを行うときは、検索、 **sysmail_event_log**電子メールの失敗に関連するイベントを表示します。 データベース メール外部プログラムの失敗を示すメッセージなど、メッセージによっては、特定の電子メールと関係していない場合があります。 特定の電子メールに関連するエラーを検索するを検索、 **mailitem_id**に障害が発生した電子メールの**sysmail_faileditems**を表示し、検索、 **sysmail_event_log**に関連するメッセージの**mailitem_id**です。 エラーが返されたとき**sp_send_dbmail**電子メールは、データベース メール システムに送信されず、およびエラーは、このビューには表示されません。  
  
 個々のアカウントで配信試行が失敗した場合は、再試行の間、メール アイテムの配信が成功または失敗するまで、データベース メールでエラー メッセージが保持されます。 Ultimate の成功した場合、すべての蓄積されたエラー ログに記録を含む個別の警告として、 **account_id**です。 これにより、電子メールが送信された場合も警告が表示されることがあります。 最終的な配信の障害発生時以前のすべての警告ログに記録せず、1 つのエラー メッセージとして、 **account_id**すべてのアカウントが失敗したため、します。  
  
## <a name="permissions"></a>権限  
 メンバーである必要がある必要があります、 **sysadmin**固定サーバー ロールまたは**DatabaseMailUserRole**このビューにアクセスするデータベース ロール。 メンバー **DatabaseMailUserRole**のメンバーではないユーザー、 **sysadmin**ロール、のみを送信するメールのイベントを表示できます。  
  
## <a name="see-also"></a>参照  
 [sysmail_faileditems &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-faileditems-transact-sql.md)   
 [データベース メール外部プログラム](../../relational-databases/database-mail/database-mail-external-program.md)  
  
  
