---
title: sp_enumeratependingschemachanges (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
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
- sp_enumeratependingschemachanges
- sp_enumeratependingschemachanges_TSQL
helpviewer_keywords:
- sp_enumeratependingschemachanges
ms.assetid: df169b21-d10a-41df-b3a1-654cfb58bc21
caps.latest.revision: 23
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: b4d54121a12322882fdf1931d1fc2188c4c0862f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spenumeratependingschemachanges-transact-sql"></a>sp_enumeratependingschemachanges (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  保留中のすべてのスキーマ変更に関する一覧を返します。 このストアド プロシージャで使用できます[sp_markpendingschemachange](../../relational-databases/system-stored-procedures/sp-markpendingschemachange-transact-sql.md)、これにより、管理者がレプリケートされないように選択した保留中のスキーマの変更をスキップします。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_enumeratependingschemachanges [ @publication = ] 'publication'   
    [ , [ @starting_schemaversion = ] starting_schemaversion ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@publication=** ] **'***パブリケーション***'**  
 パブリケーションの名前です。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [  **@starting_schemaversion=** ] *starting_schemaversion*  
 結果セットに含まれるスキーマ変更の最小数を指定します。  
  
## <a name="result-set"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**article_name**|**sysname**|スキーマの変更を適用するアーティクルの名前または**パブリケーション全体**パブリケーション全体に適用されるスキーマに変更します。|  
|**schemaversion**|**int**|保留中のスキーマ変更の数。|  
|**schematype**|**sysname**|スキーマ変更の種類を表すテキスト値。|  
|**schematext**|**nvarchar(max)**|[!INCLUDE[tsql](../../includes/tsql-md.md)] スキーマの変更を記述したとします。|  
|**schemastatus**|**nvarchar(10)**|スキーマ変更がアーティクルに対して保留になっているかどうかを示します。次のいずれかの値をとります。<br /><br /> **アクティブな**= スキーマ変更が保留中<br /><br /> **非アクティブな**= スキーマ変更がアクティブではありません<br /><br /> **スキップ**= スキーマ変更はレプリケートされません|  
|**される**|**uniqueidentifier**|スキーマ変更の識別子。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_enumeratependingschemachanges**はマージ レプリケーションで使用します。  
  
 **sp_enumeratependingschemachanges**で使用される、 [sp_markpendingschemachange](../../relational-databases/system-stored-procedures/sp-markpendingschemachange-transact-sql.md)マージ レプリケーションのサポートのためのものでは、使用する必要がありますされる場合にのみ、他の解決策など再初期化、修正に失敗しました。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_enumeratependingschemachanges**です。  
  
## <a name="see-also"></a>参照  
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [sysmergeschemachange &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/sysmergeschemachange-transact-sql.md)  
  
  
