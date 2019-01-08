---
title: sp_requestpeertopologyinfo (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_requestpeertopologyinfo
- sp_requestpeertopologyinfo_TSQL
helpviewer_keywords:
- sp_requestpeertopologyinfo
ms.assetid: 15cd28bd-5a72-41fb-ae1b-726baaa6fad5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2f3a202713931ef808aa9182404bb9d61971a7ab
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52750304"
---
# <a name="sprequestpeertopologyinfo-transact-sql"></a>sp_requestpeertopologyinfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  設定、 [MSpeer_topologyresponse](../../relational-databases/system-tables/mspeer-topologyresponse-transact-sql.md)ピア ツー ピア トランザクション レプリケーション トポロジに関する情報を含むシステム テーブル。 実行[sp_gettopologyinfo](../../relational-databases/system-stored-procedures/sp-gettopologyinfo-transact-sql.md) XML 形式でテーブルから情報を取得します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_requestpeertopologyinfo [ @publication = ] 'publication'  
        [ ,[ @requestid=] request_id OUTPUT  
```  
  
## <a name="arguments"></a>引数  
 [ @publication= ] '*publication*'  
 トポロジ全体の状態要求を実行するパブリケーションの名前を指定します。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [ @request_id=] *request_id*  
 トポロジ状態要求に割り当てられる ID 番号を指定します。 *request_id*は**int**、既定値は NULL です。 この ID で使用できる[sp_gettopologyinfo](../../relational-databases/system-stored-procedures/sp-gettopologyinfo-transact-sql.md)します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 sp_requestpeertopologyinfo は、ピア ツー ピア トランザクション レプリケーションで使用します。 実行する前に sp_requestpeertopologyinfo を実行[sp_gettopologyinfo](../../relational-databases/system-stored-procedures/sp-gettopologyinfo-transact-sql.md)します。 プロシージャはピア ツー ピア トポロジ構成ウィザードから使用されますが、トポロジ情報が必要な場合は XML 形式で直接使用することもできます。 表形式の結果を使用する場合は、クエリ、 [MSpeer_topologyresponse](../../relational-databases/system-tables/mspeer-topologyresponse-transact-sql.md)システム テーブル。  
  
## <a name="permissions"></a>アクセス許可  
 固定サーバー ロール sysadmin または固定データベース ロール db_owner のメンバーシップが必要です。  
  
## <a name="see-also"></a>参照  
 [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
