---
title: sp_scriptsubconflicttable (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
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
- sp_scriptsubconflicttable
- sp_scriptsubconflicttable_TSQL
helpviewer_keywords:
- sp_scriptsubconflicttable
ms.assetid: 13867145-3dad-47a4-8d50-a65175418479
caps.latest.revision: 22
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f9eddd0192cff32db884f153a00b0f5526d16028
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43020851"
---
# <a name="spscriptsubconflicttable-transact-sql"></a>sp_scriptsubconflicttable (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  キューに登録されたサブスクリプション アーティクルのサブスクライバー上に競合テーブルを作成するためのスクリプトを生成します。 生成されたスクリプトは、サブスクライバー側でサブスクリプション データベースについて実行されます。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_scriptsubconflicttable [@publication =] 'publication'    , [@article =] 'article'  
```  
  
## <a name="arguments"></a>引数  
 [ **@publication=**] **'***publication***'**  
 目的のアーティクルを含むパブリケーションの名前を指定します。 名前はデータベース内で一意であることが必要です。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [  **@article=**] **'***記事***'**  
 サブスクリプション アーティクルの名前を指定します。 *記事*は**sysname**、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**cmdtext**|**nvarchar (4000)**|キューに登録されたサブスクリプション アーティクルのサブスクライバー上に競合テーブルを作成するための [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトを返します。 このスクリプトは、サブスクライバー側でサブスクリプション データベースについて実行されます。|  
  
## <a name="remarks"></a>コメント  
 **sp_scriptsubconflicttable**を初期スナップショットが手動でに適用されるサブスクリプションを持つサブスクライバーに使用します。 競合テーブルは、サブスクライバー側ではオプションのテーブルです。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_scriptsubconflicttable**します。  
  
## <a name="see-also"></a>参照  
 [キュー更新における競合の検出と解決](../../relational-databases/replication/transactional/updatable-subscriptions-queued-updating-conflict-resolution.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
