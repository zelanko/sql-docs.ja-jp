---
title: sp_update_operator (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_update_operator_TSQL
- sp_update_operator
dev_langs:
- TSQL
helpviewer_keywords:
- sp_update_operator
ms.assetid: 231750a6-4828-4d03-afe6-b91d38c42ed3
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a98f5a61c76e1e6ef0cd2dc2a17a445084dd15eb
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="spupdateoperator-transact-sql"></a>sp_update_operator (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  警告およびジョブの使用に関するオペレーター (通知受信者) の情報を更新します。  
  
   ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_update_operator   
     [ @name =] 'name'   
     [ , [ @new_name = ] 'new_name' ]   
     [ , [ @enabled = ] enabled]   
     [ , [ @email_address = ] 'email_address' ]  
     [ , [ @pager_address = ] 'pager_number']   
     [ , [ @weekday_pager_start_time = ] weekday_pager_start_time ]  
     [ , [ @weekday_pager_end_time = ] weekday_pager_end_time ]   
     [ , [ @saturday_pager_start_time = ] saturday_pager_start_time ]  
     [ , [ @saturday_pager_end_time = ] saturday_pager_end_time ]   
     [ , [ @sunday_pager_start_time = ] sunday_pager_start_time ]  
     [ , [ @sunday_pager_end_time = ] sunday_pager_end_time ]   
     [ , [ @pager_days = ] pager_days ]   
     [ , [ @netsend_address = ] 'netsend_address' ]   
     [ , [ @category_name = ] 'category' ]  
```  
  
## <a name="arguments"></a>引数  
 [ @name=] '*名前*'  
 変更するオペレーターの名前を指定します。 *名前*は**sysname**、既定値はありません。  
  
 [ @new_name=] '*new_name*'  
 オペレーターの新しい名前を指定します。 この名前は一意であることが必要です。 *新しい名前*は**sysname**、既定値は NULL です。  
  
 [ @enabled=] *enabled*  
 オペレーターの現在の状態を示す数値 (**1**現在有効な場合、 **0**しない場合)。 *有効になっている*は**tinyint**、既定値は NULL です。 有効でない場合、オペレーターは警告通知を受信しません。  
  
 [ @email_address=] '*email_address*'  
 オペレーターの電子メール アドレスを指定します。 この文字列はメール システムに直接渡されます。 *email_address*は**nvarchar (100)**、既定値は NULL です。  
  
 [ @pager_address=] '*pager_number*'  
 オペレーターのポケットベルのアドレスを指定します。 この文字列はメール システムに直接渡されます。 *pager_number*は**nvarchar (100)**、既定値は NULL です。  
  
 [ @weekday_pager_start_time=] *weekday_pager_start_time*  
 月曜日から金曜日までの間で、このオペレーターに対してポケットベル通知を開始する時間を指定します。 *weekday_pager_start_time*は**int**、既定値は NULL、24 時間制の HHMMSS 形式で使用するためで入力する必要があります。  
  
 [ @weekday_pager_end_time=] *weekday_pager_end_time*  
 月曜日から金曜日までの間で、指定したオペレーターに対してポケットベル通知を終了する時間を指定します。 *エージェント*は**int**、既定値は NULL、24 時間制の HHMMSS 形式で使用するためで入力する必要があります。  
  
 [ @saturday_pager_start_time=] *saturday_pager_start_time*  
 毎週土曜日に、指定したオペレーターに対してポケットベル通知を開始する時間を指定します。 *エージェント*は**int**、既定値は NULL、24 時間制の HHMMSS 形式で使用するためで入力する必要があります。  
  
 [ @saturday_pager_end_time=] *saturday_pager_end_time*  
 毎週土曜日に、指定したオペレーターに対してポケットベル通知を終了する時間を指定します。 *@saturday_pager_end_time*は**int**、既定値は NULL、24 時間制の HHMMSS 形式で使用するためで入力する必要があります。  
  
 [ @sunday_pager_start_time=] *sunday_pager_start_time*  
 毎週日曜日に、指定したオペレーターに対してポケットベル通知を開始する時間を指定します。 *エージェント*は**int**、既定値は NULL、24 時間制の HHMMSS 形式で使用するためで入力する必要があります。  
  
 [ @sunday_pager_end_time=] *sunday_pager_end_time*  
 毎週日曜日に、指定したオペレーターに対してポケットベル通知を終了する時間を指定します。 *エージェント*は**int**、既定値は NULL、24 時間制の HHMMSS 形式で使用するためで入力する必要があります。  
  
 [ @pager_days=] *pager_days*  
 オペレーターがポケットベルのメッセージを受信できる曜日を指定します (指定した開始/終了時刻を前提とします)。 *pager_days*は**tinyint**、NULL の場合、既定値から値を指定する必要があります**0**を通じて**127**です。 *pager_days*必要となる曜日の個々 の値を加算して計算されます。 たとえば、月曜日から金曜日までからは**2**+**4**+**8**+**16** + **32** = **64**です。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|日曜日|  
|**2**|月曜日|  
|**4**|火曜日|  
|**8**|水曜日|  
|**16**|木曜日|  
|**32**|金曜日|  
|**64**|土曜日|  
  
 [ @netsend_address=] '*netsend_address*'  
 ネットワーク メッセージの送信先オペレーターのネットワーク アドレスを指定します。 *netsend_address*は**nvarchar (100)**、既定値は NULL です。  
  
 [ @category_name=] '*カテゴリ*'  
 警告のカテゴリの名前を指定します。 *カテゴリ*は**sysname**、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 sp_update_operator は、msdb データベースから実行する必要があります。  
  
## <a name="permissions"></a>権限  
 Sysadmin 固定サーバー ロールのメンバーにこのプロシージャの既定値を実行する権限です。  
  
## <a name="examples"></a>使用例  
 次の例では、無効であったオペレーターの状態を有効に更新し、ポケットベルを受信できる曜日 (月曜～金曜日、 午前 8 時～午後 5 時) を設定します。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_update_operator   
    @name = N'François Ajenstat',  
    @enabled = 1,  
    @email_address = N'françoisa',  
    @pager_address = N'5551290AW@pager.Adventure-Works.com',  
    @weekday_pager_start_time = 080000,  
    @weekday_pager_end_time = 170000,  
    @pager_days = 64 ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_add_operator &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-operator-transact-sql.md)   
 [sp_delete_operator &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-operator-transact-sql.md)   
 [sp_help_operator &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-operator-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
