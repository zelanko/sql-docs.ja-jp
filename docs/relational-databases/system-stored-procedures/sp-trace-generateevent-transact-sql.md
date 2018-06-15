---
title: sp_trace_generateevent (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_trace_generateevent_TSQL
- sp_trace_generateevent
dev_langs:
- TSQL
helpviewer_keywords:
- sp_trace_generateevent
ms.assetid: 3ef05bfb-b467-4403-89cc-6e77ef9247dd
caps.latest.revision: 35
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 398fb058ae7be57cf0c26b26e77d6e82aafd0df3
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33260658"
---
# <a name="sptracegenerateevent-transact-sql"></a>sp_trace_generateevent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ユーザー定義イベントを作成[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
>**注:** このストアド プロシージャは**いない**推奨されなくなりました。 他のすべてのトレース関連のストアド プロシージャの使用は非推奨とされます。  
  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_trace_generateevent [ @eventid = ] event_id   
     [ , [ @userinfo = ] 'user_info' ]  
     [ , [ @userdata = ] user_data ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@eventid=**] *event_id*  
 有効にするイベントの ID を指定します。 *event_id*は**int**、既定値はありません。 ID は、82 ~ 91 のセットとしてユーザー定義イベントを表すからのイベント番号のいずれかを指定する必要があります[sp_trace_setevent](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)です。  
  
 [ **@userinfo**=] **'***user_info***'**  
 イベントの理由を示すユーザー定義の文字列を指定します。この引数は省略可能です。 *user_info*は**nvarchar (128)**、既定値は NULL です。  
  
 [ **@userdata**=] *user_data*  
 イベントに対するユーザー指定のデータを指定します。この引数は省略可能です。 *user_data*は**varbinary (8000)**、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 次の表は、このストアド プロシージャの完了時に返されるコード値を示しています。  
  
|リターン コード|Description|  
|-----------------|-----------------|  
|**0**|エラーなし。|  
|**1**|不明なエラーです。|  
|**3**|指定したイベントは無効です。 イベントが存在しないか、イベントがこのストアド プロシージャに対して適切ではありません。|  
|**13**|メモリ不足。 指定した操作を実行するための十分なメモリがない場合に返されます。|  
  
## <a name="remarks"></a>解説  
 **sp_trace_generateevent**によって実行される操作の多くを実行、 **xp_trace _\*** 拡張ストアド プロシージャです。 使用して**sp_trace_generateevent**の代わりに**この**です。  
  
 ユーザー定義イベントの ID 番号のみで使用できる**sp_trace_generateevent**です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で他のイベント ID 番号を使用すると、エラーが発生します。  
  
 ストアド プロシージャのすべての SQL トレースのパラメーター (**sp_trace_xx**) は、厳密に型指定されています。 これらのパラメーターを、引数の説明で指定されている正しいデータ型で指定しないと、このストアド プロシージャではエラーが返されます。  
  
## <a name="permissions"></a>権限  
 ユーザーに ALTER TRACE 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、ユーザーが構成できるイベントをサンプル テーブルに作成します。  
  
```  
--Create a sample table.  
CREATE TABLE user_config_test(col1 int, col2 char(10));  
  
--DROP the trigger if it already exists.  
IF EXISTS  
   (SELECT * FROM sysobjects WHERE name = 'userconfig_trg')  
   DROP TRIGGER userconfig_trg;  
  
--Create an ON INSERT trigger on the sample table.  
CREATE TRIGGER userconfig_trg  
   ON user_config_test FOR INSERT;  
AS  
EXEC master..sp_trace_generateevent  
   @event_class = 82, @userinfo = N'Inserted row into user_config_test';  
  
--When an insert action happens, the user-configurable event fires. If   
you were capturing the event id=82, you will see it in the Profiler output.  
INSERT INTO user_config_test VALUES(1, 'abc');  
```  
  
## <a name="see-also"></a>参照  
 [sys.fn_trace_geteventinfo &#40;TRANSACT-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-geteventinfo-transact-sql.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [SQL トレース (SQL Trace)](../../relational-databases/sql-trace/sql-trace.md)  
  
  
