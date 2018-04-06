---
title: sp_posttracertoken (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedur+I741es
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- posttracerttoken
- posttracerttoken_TSQL
- sp_posttracertoken
- sp_posttracertoken_TSQL
helpviewer_keywords:
- sp_posttracertoken
ms.assetid: 24da5cd2-1c45-475e-93db-5bdf660f1c2c
caps.latest.revision: 28
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 79102a0a4c9e0b2122b23f01a7e7808c0d610967
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spposttracertoken-transact-sql"></a>sp_posttracertoken (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  このプロシージャは、パブリッシャー側のトランザクション ログにトレーサー トークンを送信し、待機時間の統計を追跡する処理を開始します。 情報が記録されるタイミングは、トレーサー トークンがトランザクション ログに書き込まれたとき、ログ リーダー エージェントに処理されたとき、およびディストリビューション エージェントによって適用されたときです。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。 詳細については、「 [トランザクション レプリケーションの待機時間の計測および接続の検証](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)」を参照してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_posttracertoken [ @publication = ] 'publication'   
    [ , [ @tracer_token_id = ] tracer_token_id OUTPUT  
    [ , [ @publisher = ] 'publisher'   
```  
  
## <a name="arguments"></a>引数  
 [ **@publication**=] **'***パブリケーション***'**  
 待機時間を計測しているパブリケーションの名前を指定します。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [  **@tracer_token_id=** ] *tracer_token_id***出力**  
 挿入されたトレーサー トークンの ID です。 *tracer_token_id*は**int**既定値は NULL の場合、これは、出力パラメーターです。 この値を実行するために使用できます[sp_helptracertokenhistory (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql.md)または[sp_deletetracertokenhistory (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-deletetracertokenhistory-transact-sql.md)最初実行することがなく[sp_helptracertokens (& a) #40 です。TRANSACT-SQL と #41 です](../../relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql.md)。  
  
 [  **@publisher=** ] **'***パブリッシャー***'**  
 指定以外[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。 *パブリッシャー*は**sysname**、既定値は NULL を指定しないでと、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_posttracertoken**トランザクション レプリケーションで使用します。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_tracertokens](../../relational-databases/replication/codesnippet/tsql/sp-posttracertoken-trans_1.sql)]  
  
## <a name="permissions"></a>Permissions  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_posttracertoken**です。  
  
## <a name="see-also"></a>参照  
 [トランザクション レプリケーションの待機時間の計測および接続の検証](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  
  
