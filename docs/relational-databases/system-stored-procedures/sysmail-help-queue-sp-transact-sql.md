---
title: sysmail_help_queue_sp (TRANSACT-SQL) |Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 76f51489a449c44dd7d43bab75d504f68e946374
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47796518"
---
# <a name="sysmailhelpqueuesp-transact-sql"></a>sysmail_help_queue_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベース メールには、メール キューと状態キューの 2 つのキューがあります。 メール キューには、送信待ちのメール アイテムが格納され、 状態キューには、送信済みのアイテムの状態が格納されます。 このストアド プロシージャを使用すると、メール キューや状態キューの状態を確認できます。 場合、パラメーター **@queue_type**が指定されていない、ストアド プロシージャは、各キューの 1 つの行を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sysmail_help_queue_sp  [ @queue_type = ] 'queue_type'  
```  
  
## <a name="arguments"></a>引数  
 [ **@queue_type** =] **'***queue_type***'**  
 省略可能な引数として指定された型の電子メールを削除する、 *queue_type*します。 *queue_type*は**nvarchar (6)** 既定値はありません。 有効なエントリは**メール**と**状態**します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-set"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**queue_type**|**nvarchar(6)**|キューの種類。 指定できる値は**メール**と**状態**します。|  
|**length**|**int**|指定したキュー内のメール アイテムの数。|  
|**state**|**nvarchar(64)**|監視の状態。 指定できる値は**INACTIVE** (キューはアクティブなされません)**通知**(キューがされている受信)、および**RECEIVES_OCCURRING** (キューは受信中)。|  
|**last_empty_rowset_time**|**DATETIME**|キューが最後に空になった日時。 24 時間形式、GMT タイム ゾーンで表されます。|  
|**last_activated_time**|**DATETIME**|キューが最後にアクティブ化された日時。 24 時間形式、GMT タイム ゾーンで表されます。|  
  
## <a name="remarks"></a>コメント  
 データベース メールのトラブルシューティングを行うとき**sysmail_help_queue_sp**と最後に、キューの状態のアクティブ化する項目の数は、キューにあるを参照してください。  
  
## <a name="permissions"></a>アクセス許可  
 既定のメンバーだけで、 **sysadmin**固定サーバー ロールは、このプロシージャを使用できます。  
  
## <a name="examples"></a>使用例  
 次の例では、メール キューと状態キュー両方を返します。  
  
```  
EXECUTE msdb.dbo.sysmail_help_queue_sp ;  
GO  
```  
  
 次は、結果セットのサンプルです。length 列に編集が加えられています。  
  
```  
queue_type length      state              last_empty_rowset_time  last_activated_time  
---------- -------- ------------------ ----------------------- -----------------------  
mail       0        RECEIVES_OCCURRING 2005-10-07 21:14:47.010 2005-10-10 20:52:51.517  
status     0        INACTIVE           2005-10-07 21:04:47.003 2005-10-10 21:04:47.003  
  
(2 row(s) affected)  
  
```  
  
## <a name="see-also"></a>参照  
 [データベース メール](../../relational-databases/database-mail/database-mail.md)  
  
  
