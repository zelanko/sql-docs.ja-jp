---
title: "sp_scriptpublicationcustomprocs (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_scriptpublicationcustomprocs
- sp_scriptpublicationcustomprocs_TSQL
helpviewer_keywords:
- sp_scriptpublicationcustomprocs
ms.assetid: b06102d5-4284-4834-b126-bc0baea49be5
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 258a82812bbda7f572bb56178dd65973769ce357
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spscriptpublicationcustomprocs-transact-sql"></a>sp_scriptpublicationcustomprocs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  自動生成カスタム プロシージャ スキーマ オプションが有効になっているパブリケーションの、すべてのテーブル アーティクルに対し、カスタム INSERT、UPDATE、DELETE プロシージャのスクリプトを作成します。 **sp_scriptpublicationcustomprocs**はスナップショットが手動で適用される対象のサブスクリプションを設定するために特に便利です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_scriptpublicationcustomprocs [ @publication = ] 'publication_name'  
```  
  
## <a name="arguments"></a>引数  
 [  **@publication** =] **'***publication_name***'**  
 パブリケーションの名前です。 *publication_name*は**sysname**既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 1 つので構成される結果セットを返します**nvarchar (4000)**列です。 この結果セットは、カスタム ストアド プロシージャの作成に必要な、完全な CREATE PROCEDURE ステートメントを構成します。  
  
## <a name="remarks"></a>解説  
 自動生成カスタム プロシージャ (0x2) スキーマ オプションが有効になっていない場合、アーティクルに対してカスタム プロシージャのスクリプトは作成されません。  
  
 次の手順を使用**sp_scriptpublicationcustomprocs**サブスクライバーでプロシージャを作成し、直接実行する必要があります。  
  
 **sp_script_reconciliation_delproc**  
  
 **sp_script_reconciliation_insproc**  
  
 **sp_script_reconciliation_vdelproc**  
  
 **sp_script_reconciliation_xdelproc**  
  
 **sp_scriptdelproc**  
  
 **sp_scriptinsproc**  
  
 **sp_scriptmappedupdproc**  
  
 **sp_scriptupdproc**  
  
 **sp_scriptvdelproc**  
  
 **sp_scriptvupdproc**  
  
 **sp_scriptxdelproc**  
  
 **sp_scriptxupdproc**  
  
## <a name="permissions"></a>Permissions  
 実行する権限が与えられて**パブリック**; のメンバーへのアクセスを制限するこのストアド プロシージャ内でセキュリティ チェックが実行される、 **sysadmin**固定サーバー ロールと**作業所有者**現在のデータベースの固定データベース ロール。  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
