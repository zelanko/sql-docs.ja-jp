---
title: sp_posttracertoken (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- posttracerttoken
- posttracerttoken_TSQL
- sp_posttracertoken
- sp_posttracertoken_TSQL
helpviewer_keywords:
- sp_posttracertoken
ms.assetid: 24da5cd2-1c45-475e-93db-5bdf660f1c2c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7629c25264f0b45d68e29e947b1d5c40d02707e7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "72041183"
---
# <a name="sp_posttracertoken-transact-sql"></a>sp_posttracertoken (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  このプロシージャは、パブリッシャー側のトランザクション ログにトレーサー トークンを送信し、待機時間の統計を追跡する処理を開始します。 情報が記録されるタイミングは、トレーサー トークンがトランザクション ログに書き込まれたとき、ログ リーダー エージェントに処理されたとき、およびディストリビューション エージェントによって適用されたときです。 このストアドプロシージャは、パブリッシャー側でパブリケーションデータベースに対して実行されます。 詳細については、「 [トランザクション レプリケーションの待機時間の計測および接続の検証](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)」を参照してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_posttracertoken [ @publication = ] 'publication'   
    [ , [ @tracer_token_id = ] tracer_token_id OUTPUT  
    [ , [ @publisher = ] 'publisher'   
```  
  
## <a name="arguments"></a>引数  
`[ @publication = ] 'publication'`待機時間を測定するパブリケーションの名前を指定します。 *publication*は**sysname**,、既定値はありません。  
  
`[ @tracer_token_id = ] _tracer_token_id OUTPUT`挿入されるトレーサートークンの ID を示します。 *tracer_token_id*は**int**で、既定値は NULL です。これは出力パラメーターです。 この値を使用して[sp_helptracertokenhistory &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql.md)を実行したり、 [transact-sql &#40;を](../../relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql.md)最初に実行せずに transact-sql&#41;を[sp_deletetracertokenhistory](../../relational-databases/system-stored-procedures/sp-deletetracertokenhistory-transact-sql.md)することができます。  
  
`[ @publisher = ] 'publisher'`以外[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のパブリッシャーを指定します。 *publisher*は**sysname**であり、既定値は NULL です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーに対して指定することはできません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>Remarks  
 **sp_posttracertoken**は、トランザクションレプリケーションで使用します。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_tracertokens](../../relational-databases/replication/codesnippet/tsql/sp-posttracertoken-trans_1.sql)]  
  
## <a name="permissions"></a>アクセス許可  
 **Sp_posttracertoken**を実行できるのは、固定サーバーロール**sysadmin**または固定データベースロール**db_owner**のメンバーだけです。  
  
## <a name="see-also"></a>参照  
 [トランザクション レプリケーションの待機時間の計測および接続の検証](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  
  
