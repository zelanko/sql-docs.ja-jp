---
title: sp_scriptpublicationcustomprocs (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_scriptpublicationcustomprocs
- sp_scriptpublicationcustomprocs_TSQL
helpviewer_keywords:
- sp_scriptpublicationcustomprocs
ms.assetid: b06102d5-4284-4834-b126-bc0baea49be5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2b57ae49875c07607e153b793c76db31d5dd347b
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52808644"
---
# <a name="spscriptpublicationcustomprocs-transact-sql"></a>sp_scriptpublicationcustomprocs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  自動生成カスタム プロシージャ スキーマ オプションが有効になっているパブリケーションの、すべてのテーブル アーティクルに対し、カスタム INSERT、UPDATE、DELETE プロシージャのスクリプトを作成します。 **sp_scriptpublicationcustomprocs**は、スナップショットが手動で適用される対象のサブスクリプションを設定するために特に便利です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_scriptpublicationcustomprocs [ @publication = ] 'publication_name'  
```  
  
## <a name="arguments"></a>引数  
 [ **@publication**=] **'***publication_name***'**  
 パブリケーションの名前です。 *publication_name*は**sysname**既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 結果セットを返しますが、1 つから成る**nvarchar (4000)** 列。 この結果セットは、カスタム ストアド プロシージャの作成に必要な、完全な CREATE PROCEDURE ステートメントを構成します。  
  
## <a name="remarks"></a>コメント  
 自動生成カスタム プロシージャ (0x2) スキーマ オプションが有効になっていない場合、アーティクルに対してカスタム プロシージャのスクリプトは作成されません。  
  
 次の手順を使って**sp_scriptpublicationcustomprocs**サブスクライバーでプロシージャを作成して、直接実行する必要があります。  
  
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
  
## <a name="permissions"></a>アクセス許可  
 実行する権限が与えられて**パブリック**; のメンバーにアクセスを制限するこのストアド プロシージャ内でセキュリティ チェックが実行される、 **sysadmin**固定サーバー ロールと**作業所有者**現在のデータベースの固定データベース ロール。  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
