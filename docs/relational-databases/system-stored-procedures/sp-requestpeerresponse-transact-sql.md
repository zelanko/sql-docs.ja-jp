---
title: sp_requestpeerresponse (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_requestpeerresponse_TSQL
- sp_requestpeerresponse
helpviewer_keywords:
- sp_requestpeerresponse
ms.assetid: cbe13c22-4d7d-4a36-b194-7a13ce68ef27
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 300ff762ee7fbcefcd593cf3d7dd9ff0e81fcfed
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47821640"
---
# <a name="sprequestpeerresponse-transact-sql"></a>sp_requestpeerresponse (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ピア ツー ピア トポロジ内にある 1 つのノードから実行した場合、トポロジ内にある他の各ノードからの応答を要求します。 このプロシージャを実行し、返された応答を確認することで、先に実行したコマンドが、応答を返したノードに配信されたことを確認できます。 このストアド プロシージャは、任意のデータベース上にある、要求を発行するノードで実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_requestpeerresponse [ @publication = ] 'publication'  
    [ , [ @description = ] 'description'  
    [ , [ @request_id = ] request_id OUTPUT ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@publication**=] **'***パブリケーション***'**  
 ピア ツー ピア トポロジ内の、状態を確認するパブリケーションの名前を指定します。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [ **@description**=] **'***説明***'**  
 個々の状態要求の識別に使用できるユーザー定義情報 *説明*は**nvarchar (4000)**、既定値は NULL です。  
  
 [ **@request_id** =] *request_id*  
 新しい要求の ID を返します。 *request_id*は**int**は出力パラメーター。 実行するときに、この値を使用できます[sp_helppeerresponses &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql.md)状態要求に応答するすべての表示にします。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_requestpeerresponse**はピア ツー ピア トランザクション レプリケーションで使用します。  
  
 **sp_requestpeerresponse**ピア ツー ピア トポロジでパブリッシュされたデータベースを復元する前に、すべてのコマンドがその他のすべてのノードで受信されたことを確認するために使用します。 また、ノードがオフラインの間に行われたデータ定義言語 (DDL) の変更をレプリケートするときに、これらの変更が他のノードに到達する時間を推定する場合にも使用できます。  
  
 **sp_requestpeerresponse**ユーザー定義のトランザクション内で実行することはできません。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_requestpeerresponse**します。  
  
## <a name="see-also"></a>参照  
 [sp_deletepeerrequesthistory &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-deletepeerrequesthistory-transact-sql.md)   
 [sp_helppeerrequests &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppeerrequests-transact-sql.md)  
  
  
