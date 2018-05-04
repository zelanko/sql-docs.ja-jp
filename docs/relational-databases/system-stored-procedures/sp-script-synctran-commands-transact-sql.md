---
title: sp_script_synctran_commands (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_script_synctran_commands
- sp_script_synctran_commands_TSQL
helpviewer_keywords:
- sp_script_synctran_commands
ms.assetid: f132694a-dd05-405b-9d84-21acce9e564a
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 66156ab677aa06c4f84c626fc8e462b2c4596d02
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spscriptsynctrancommands-transact-sql"></a>sp_script_synctran_commands (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  含むスクリプトを生成、 **sp_addsynctrigger**更新可能なサブスクリプションのサブスクライバーで適用される呼び出しです。 1 つを使用する必要がある**sp_addsynctrigger**パブリケーションの各アーティクルに呼び出します。 生成されるスクリプトにも含まれています、 **sp_addqueued_artinfo**作成の呼び出し、 **MSsubsciption_articles**キュー パブリケーションの処理に必要なテーブルです。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_script_synctran_commands [@publication = ] 'publication'  
    [ , [@article = ] 'article']  
```  
  
## <a name="arguments"></a>引数  
 [ **@publication** =] **'***パブリケーション***'**  
 スクリプト作成の対象となるパブリケーションの名前を指定します。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [ **@article** =] **'***記事***'**  
 スクリプト作成の対象となるアーティクルの名前を指定します。 *記事*は**sysname**、既定値は**すべて**、すべてのアーティクルがスクリプト化します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="results-set"></a>結果セット  
 **sp_script_synctran_commands** 、1 つので構成される結果セットを返します**nvarchar (4000)** 列です。 結果セットのフォーム、完全なスクリプトを両方を作成するために必要な**sp_addsynctrigger**と**sp_addqueued_artinfo**サブスクライバーで適用される呼び出しです。  
  
## <a name="remarks"></a>解説  
 **sp_script_synctran_commands**は、スナップショットおよびトランザクション レプリケーションで使用します。  
  
 **sp_addqueued_artinfo**キュー更新サブスクリプションに対して使用します。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_script_synctran_commands**です。  
  
## <a name="see-also"></a>参照  
 [sp_addsynctriggers &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsynctriggers-transact-sql.md)   
 [sp_addqueued_artinfo &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addqueued-artinfo-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
