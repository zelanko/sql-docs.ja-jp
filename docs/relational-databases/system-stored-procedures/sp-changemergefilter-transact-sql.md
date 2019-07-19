---
title: sp_changemergefilter (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changemergefilter_TSQL
- sp_changemergefilter
helpviewer_keywords:
- sp_changemergefilter
ms.assetid: e08fdfdd-d242-4e85-817b-9f7a224fe567
author: stevestein
ms.author: sstein
ms.openlocfilehash: e0c38af1089a1d59c9964e39aecca6b1773a8e22
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68124891"
---
# <a name="spchangemergefilter-transact-sql"></a>sp_changemergefilter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  いくつかのマージ フィルター プロパティを変更します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_changemergefilter [ @publication= ] 'publication'  
        , [ @article= ] 'article'  
        , [ @filtername= ] 'filtername'  
        , [ @property= ] 'property'  
        , [ @value= ] 'value'  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
```  
  
## <a name="arguments"></a>引数  
`[ @publication = ] 'publication'` パブリケーションの名前です。 *パブリケーション* は **sysname** 、既定値はありません。  
  
`[ @article = ] 'article'` アーティクルの名前です。 *記事*は**sysname**、既定値はありません。  
  
`[ @filtername = ] 'filtername'` フィルターの現在の名前です。 *filtername*は**sysname**、既定値はありません。  
  
`[ @property = ] 'property'` 変更するプロパティの名前です。 *プロパティ*は**sysname**、既定値はありません。  
  
`[ @value = ] 'value'` 指定したプロパティの新しい値です。 *値*は**nvarchar (1000)** 、既定値はありません。  
  
 このテーブルには、記事、これらのプロパティの値のプロパティについて説明します。  
  
|プロパティ|値|説明|  
|--------------|-----------|-----------------|  
|**filter_type**|**1**|結合フィルター。<br /><br /> このオプションがサポートするために必要な[!INCLUDE[ssEW](../../includes/ssew-md.md)]サブスクライバー。|  
||**2**|論理レコード リレーションシップです。|  
||**3**|結合フィルターは論理レコードのリレーションシップもです。|  
|**filtername**||フィルターの名前。|  
|**join_articlename**||結合アーティクルの名前です。|  
|**join_filterclause**||フィルター句。|  
|**join_unique_key**|**true**|結合は、一意なキーに基づいて行われます。|  
||**false**|結合は、一意のキーにはありません。|  
  
`[ @force_invalidate_snapshot = ] force_invalidate_snapshot` このストアド プロシージャが実行する操作が既存のスナップショットが無効になることを確認します。 *更によって*は、**ビット**、既定値は、 **0**します。  
  
 **0**スナップショットが無効であることをマージ アーティクルへの変更が発生しないことを指定します。 ストアド プロシージャは、変更は、新しいスナップショットを必要になることを検出する場合は、エラーが発生し、変更は行われません。  
  
 **1**手段に、マージ アーティクルへの変更には、スナップショットを無効になる可能性がありますを新しいスナップショットを必要とする既存のサブスクリプションがある場合は、不使用とマークするのには、既存のスナップショットを新しいスナップショットを生成のアクセス許可を付与します。  
  
`[ @force_reinit_subscription = ] force_reinit_subscription` このストアド プロシージャが実行されるアクションでは、既存のサブスクリプションの再初期化される場合がありますかを確認します。 *更によって*は、**ビット**、既定値は**0**します。  
  
 **0**マージ アーティクルへの変更では、サブスクリプションを再初期化するのには発生しないことを指定します。 ストアド プロシージャは、変更が既存のサブスクリプションを再初期化する必要になることを検出する場合は、エラーが発生し、変更は行われません。  
  
 **1**既存のサブスクリプションが初期化されることにより、マージ アーティクルへの変更が発生するサブスクリプションを再初期化を許可します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_changemergefilter**はマージ レプリケーションで使用します。  
  
 マージ アーティクルのフィルターを変更すると、再作成する、存在する場合、スナップショットが必要です。 これには、実行するには、 **@force_invalidate_snapshot** に**1**します。 また、このアーティクルに対するサブスクリプションがある場合、サブスクリプションを再初期化する必要があります。 これは、設定で、 **@force_reinit_subscription** に**1**します。  
  
 論理レコードを使用するには、パブリケーションとアーティクルが多くの要件を満たしている必要があります。 詳細については、「[Group Changes to Related Rows with Logical Records](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md)」 (論理レコードによる関連行への変更のグループ化) を参照してください。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_changemergefilter**します。  
  
## <a name="see-also"></a>関連項目  
 [パブリケーションとアーティクルのプロパティの変更](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [sp_addmergefilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md)   
 [sp_dropmergefilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dropmergefilter-transact-sql.md)   
 [sp_helpmergefilter &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergefilter-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
