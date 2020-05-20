---
title: sp_requestpeertopologyinfo (Transact-sql) |Microsoft Docs
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 61439aeb9fd4a58d8b003473a4e55fa19ca06a36
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82824341"
---
# <a name="sp_requestpeertopologyinfo-transact-sql"></a>sp_requestpeertopologyinfo (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [MSpeer_topologyresponse](../../relational-databases/system-tables/mspeer-topologyresponse-transact-sql.md)システムテーブルに、ピアツーピアトランザクションレプリケーショントポロジに関する情報を設定します。 [Sp_gettopologyinfo](../../relational-databases/system-stored-procedures/sp-gettopologyinfo-transact-sql.md)を実行して、XML 形式でテーブルから情報を取得します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_requestpeertopologyinfo [ @publication = ] 'publication'  
        [ ,[ @requestid=] request_id OUTPUT  
```  
  
## <a name="arguments"></a>引数  
 [ @publication =] '*パブリケーション*'  
 トポロジ全体の状態要求を実行するパブリケーションの名前を指定します。 *publication*は**sysname**,、既定値はありません。  
  
 [ @request_id =] *request_id*  
 トポロジ状態要求に割り当てられている ID 番号を指定します。 *request_id*は**int**,、既定値は NULL です。 この ID は[sp_gettopologyinfo](../../relational-databases/system-stored-procedures/sp-gettopologyinfo-transact-sql.md)で使用できます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>Remarks  
 sp_requestpeertopologyinfo は、ピア ツー ピア トランザクション レプリケーションで使用します。 [Sp_gettopologyinfo](../../relational-databases/system-stored-procedures/sp-gettopologyinfo-transact-sql.md)を実行する前に sp_requestpeertopologyinfo を実行してください。 これらの手順は、ピアツーピアトポロジ構成ウィザードで使用されますが、XML 形式でトポロジ情報が必要な場合は、直接使用することもできます。 表形式の結果を優先する場合は、 [MSpeer_topologyresponse](../../relational-databases/system-tables/mspeer-topologyresponse-transact-sql.md)システムテーブルに対してクエリを実行します。  
  
## <a name="permissions"></a>アクセス許可  
 Sysadmin 固定サーバーロールまたは db_owner 固定データベースロールのメンバーシップが必要です。  
  
## <a name="see-also"></a>参照  
 [ピアツーピアトランザクションレプリケーション](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
