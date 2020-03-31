---
title: sysmail_help_queue_sp (トランザクション-SQL) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_help_queue_sp
- sysmail_help_queue_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_help_queue_sp
ms.assetid: 94840482-112c-4654-b480-9b456c4c2bca
author: stevestein
ms.author: sstein
ms.openlocfilehash: d506d7ea841e211d9ab6fb0715a6a9359cefa83d
ms.sourcegitcommit: 4baa8d3c13dd290068885aea914845ede58aa840
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/13/2020
ms.locfileid: "79289950"
---
# <a name="sysmail_help_queue_sp-transact-sql"></a>sysmail_help_queue_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベース メールには、メール キューと状態キューの 2 つのキューがあります。 メール キューには、送信待ちのメール アイテムが格納され、 状態キューには、送信済みのアイテムの状態が格納されます。 このストアド プロシージャを使用すると、メール キューまたはステータス キューの状態を表示できます。 パラメーター queue_type**\@** が指定されていない場合、ストアド プロシージャはキューごとに 1 行を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sysmail_help_queue_sp  [ @queue_type = ] 'queue_type'  
```  
  
## <a name="arguments"></a>引数  
`[ @queue_type = ] 'queue_type'`省略可能な引数は *、queue_type*として指定された種類の電子メールを削除します。 *queue_type*は**nvarchar(6) で**、デフォルトはありません。 有効なエントリは **、メール**と**ステータスです**。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-set"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**queue_type**|**nvarchar(6)**|キューの種類。 指定できる値は **、メール**と**ステータス です**。|  
|**length**|**Int**|指定したキュー内のメール アイテムの数。|  
|**state**|**nvarchar(64)**|モニタの状態。 可能な値は **、INACTIVE** (キューが非アクティブ **)、NOTIFIED** (キューが受信通知された受信が発生しました)、および**RECEIVES_OCCURRING** (キューが受信中) です。|  
|**last_empty_rowset_time**|**Datetime**|キューが最後に空だった日時。 軍事時形式と GMT タイム ゾーン。|  
|**last_activated_time**|**Datetime**|キューが最後にアクティブになった日時。 軍事時形式と GMT タイム ゾーン。|  
  
## <a name="remarks"></a>解説  
 データベース メールのトラブルシューティングを行う場合は **、sysmail_help_queue_sp**を使用して、キュー内のアイテム数、キューの状態、および最後にアクティブ化された項目の数を確認します。  
  
## <a name="permissions"></a>アクセス許可  
 既定では **、sysadmin**固定サーバー ロールのメンバーのみがこの手順にアクセスできます。  
  
## <a name="examples"></a>使用例  
 次の例では、メール キューと状態キュー両方を返します。  
  
```  
EXECUTE msdb.dbo.sysmail_help_queue_sp ;  
GO  
```  
  
 これは、長さのために編集されたサンプル結果セットです。  
  
```  
queue_type length      state              last_empty_rowset_time  last_activated_time  
---------- -------- ------------------ ----------------------- -----------------------  
mail       0        RECEIVES_OCCURRING 2005-10-07 21:14:47.010 2005-10-10 20:52:51.517  
status     0        INACTIVE           2005-10-07 21:04:47.003 2005-10-10 21:04:47.003  
  
(2 row(s) affected)  
  
```  
  
## <a name="see-also"></a>関連項目  
 [データベース メール](../../relational-databases/database-mail/database-mail.md)  
  
  
