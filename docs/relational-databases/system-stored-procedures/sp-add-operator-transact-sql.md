---
title: sp_add_operator (TRANSACT-SQL) |Microsoft ドキュメント
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
- sp_add_operator
- sp_add_operator_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_operator
ms.assetid: 817cd98a-4dff-4ed8-a546-f336c144d1e0
caps.latest.revision: 26
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c91f79397a84f6277f4bb891144a5fceb40d02ce
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="spaddoperator-transact-sql"></a>sp_add_operator (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  警告とジョブで使用するオペレーター (通知受信者) を作成します。  
  
 
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_add_operator [ @name = ] 'name'   
     [ , [ @enabled = ] enabled ]   
     [ , [ @email_address = ] 'email_address' ]   
     [ , [ @pager_address = ] 'pager_address' ]   
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
 [ **@name=** ] **'***name***'**  
 オペレーター (通知受信者) の名前を指定します。 この名前は一意であり、割合を含めることはできません (**%**) 文字です。 *名前*は**sysname**、既定値はありません。  
  
 [ **@enabled=** ] *enabled*  
 オペレーターの現在の状態を示します。 *有効になっている*は**tinyint**、既定値は**1** (有効) です。 場合**0**オペレーターが有効でないと通知を受信しません。  
  
 [ **@email_address=** ] **'***email_address***'**  
 オペレーターの電子メール アドレスを指定します。 この文字列はメール システムに直接渡されます。 *email_address*は**nvarchar (100)**、既定値は NULL です。  
  
 実際の電子メール アドレスまたはの別名のいずれかを指定することができます*email_address*です。 以下に例を示します。  
  
 '**jdoe**'または'**jdoe@xyz.com**'  
  
> [!NOTE]  
>  データベース メールには電子メール アドレスを使用する必要があります。  
  
 [ **@pager_address=** ] **'***pager_address***'**  
 オペレーターのポケットベルのアドレスを指定します。 この文字列はメール システムに直接渡されます。 *pager_address*は**narchar (100)**、既定値は NULL です。  
  
 [ **@weekday_pager_start_time=** ] *weekday_pager_start_time*  
 時刻を[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント ポケットベルによる通知に指定したオペレーターに送信平日に、月曜日から金曜日までからです。 *weekday_pager_start_time*は**int**、既定値は**090000**午前 9時 00分を示します を 24 時間形式で表したものです。HHMMSS 形式で入力する必要があります。  
  
 [ **@weekday_pager_end_time=** ] *weekday_pager_end_time*  
 時刻を**SQLServerAgent**サービス不要になったポケットベルによる通知に指定したオペレーターに送信平日に、月曜日から金曜日までからです。 *エージェント*は**int**、制で表した 180000、既定値を示す午後 6時 00分 を 24 時間形式で表したものです。HHMMSS 形式で入力する必要があります。  
  
 [ **@saturday_pager_start_time =**] *saturday_pager_start_time*  
 時刻を**SQLServerAgent**サービスは、毎週土曜日に、指定したオペレーターにポケットベルの通知を送信します。 *エージェント*は**int**090000、既定値はことを示します午前 9時 00分 を 24 時間形式で表したものです。HHMMSS 形式で入力する必要があります。  
  
 [ **@saturday_pager_end_time=** ] *saturday_pager_end_time*  
 時刻を**SQLServerAgent**サービス不要になったポケットベルの通知送信指定したオペレーターに対して毎週土曜日です。 *@saturday_pager_end_time*は**int**、既定値は**180000**、午後 6 時 00 分を示します を 24 時間形式で表したものです。HHMMSS 形式で入力する必要があります。  
  
 [ **@sunday_pager_start_time=** ] *sunday_pager_start_time*  
 時刻を**SQLServerAgent**サービスが、指定したオペレーターに対して毎週日曜日ポケットベルの通知を送信します。 *エージェント*は**int**、既定値は**090000**午前 9時 00分を示します を 24 時間形式で表したものです。HHMMSS 形式で入力する必要があります。  
  
 [ **@sunday_pager_end_time =**] *sunday_pager_end_time*  
 時刻を**SQLServerAgent**サービス不要になったポケットベルの通知送信指定したオペレーターに対して毎週日曜日です。 *エージェント*は**int**、既定値は**180000**、午後 6 時 00 分を示します を 24 時間形式で表したものです。HHMMSS 形式で入力する必要があります。  
  
 [ **@pager_days=** ] *pager_days*  
 指定された開始時刻から終了時刻までの間に、オペレーターがポケットベルの通知を受信できる曜日を表す数値を指定します。 *pager_days*は**tinyint**、既定値は**0**ページの受信に使用できることはありませんが、演算子をことを示します。 有効な値は**0**を通じて**127**です。 *pager_days*必要となる曜日の個々 の値を加算して計算されます。 たとえば、月曜日から金曜日までからは**2**+**4**+**8**+**16** + **32** = **62**です。 次の表は、各曜日に対する値の一覧です。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|日曜日|  
|**2**|月曜日|  
|**4**|火曜日|  
|**8**|水曜日|  
|**16**|木曜日|  
|**32**|金曜日|  
|**64**|土曜日|  
  
 [ **@netsend_address=** ] **'***netsend_address***'**  
 ネットワーク メッセージの送信先オペレーターのネットワーク アドレスを指定します。 *netsend_address*は**nvarchar (100)**、既定値は NULL です。  
  
 [ **@category_name=** ] **'***category***'**  
 オペレーターのカテゴリの名前を指定します。 *カテゴリ*は**sysname**、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 **sp_add_operator**から実行する必要があります、 **msdb**データベース。  
  
 ポケットベルによる通知は電子メール システムによりサポートされます。ポケットベルによる通知を使用するには、電子メールからポケットベルへの通知機能を持つ電子メール システムを使用する必要があります。  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] は、ジョブを簡単に管理できるグラフィカルなツールです。ジョブのインフラストラクチャを作成し、管理するには、このツールを使用することをお勧めします。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_add_operator**です。  
  
## <a name="examples"></a>使用例  
 次の例では、`danwi` に対してオペレーター情報を設定します。 オペレーターは有効になっています。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントは、月曜日から金曜日の午前 8 時から午後 5 時まで、 ポケットベルによる通知を送信します。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_operator  
    @name = N'Dan Wilson',  
    @enabled = 1,  
    @email_address = N'danwi',  
    @pager_address = N'5551290AW@pager.Adventure-Works.com',  
    @weekday_pager_start_time = 080000,  
    @weekday_pager_end_time = 170000,  
    @pager_days = 62 ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_delete_operator &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-operator-transact-sql.md)   
 [sp_help_operator &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-operator-transact-sql.md)   
 [sp_update_operator &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-operator-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
