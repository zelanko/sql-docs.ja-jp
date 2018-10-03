---
title: sp_mergearticlecolumn (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_mergearticlecolumn
- sp_mergearticlecolumn_TSQL
helpviewer_keywords:
- sp_mergearticlecolumn
ms.assetid: b4f2b888-e094-4759-a472-d893638995eb
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 479ac5e7d9a1d451ea489a3a43c0ff481a6a121f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47837026"
---
# <a name="spmergearticlecolumn-transact-sql"></a>sp_mergearticlecolumn (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  マージ パブリケーションを列方向にパーティション分割します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_mergearticlecolumn [ @publication = ] 'publication'  
        , [ @article = ] 'article'  
    [ , [ @column = ] 'column'  
    [ , [ @operation = ] 'operation'   
    [ , [ @schema_replication = ] 'schema_replication' ]  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]   
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]   
```  
  
## <a name="arguments"></a>引数  
 [  **@publication =**] **'***パブリケーション***'**  
 パブリケーションの名前です。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [  **@article =**] **'***記事***'**  
 パブリケーションのアーティクルの名前です。 *記事*は**sysname**、既定値はありません。  
  
 [  **@column =**] **'***列***'**  
 列方向にパーティション分割する列の名前を指定します。 *列*は**sysname**、既定値は NULL です。 値が NULL で `@operation = N'add'` の場合、既定ではソース テーブルのすべての列がアーティクルに追加されます。 *列*ときに、NULL にすることはできません*操作*に設定されている**ドロップ**します。 アーティクルから列を除外するには実行**sp_mergearticlecolumn**指定と*列*と`@operation = N'drop'`を削除するには、各列の指定した*記事*.  
  
 [  **@operation =**] **'***操作***'**  
 レプリケーションの状態を指定します。 *操作*は**nvarchar (4)**、既定値は ADD です。 **追加**レプリケーションする列をマークします。 **drop**列をクリアします。  
  
 [  **@schema_replication=**] **'***schema_replication***'**  
 マージ エージェントが実行されたときにスキーマの変更を通知します。 *schema_replication*は**nvarchar (5)**、既定値は FALSE。  
  
> [!NOTE]  
>  のみ**FALSE**はサポートされて*schema_replication*します。  
  
 [  **@force_invalidate_snapshot =** ]*更によって*  
 スナップショットを無効にする機能を有効または無効にします。 *更によって*は、**ビット**、既定値は**0**します。  
  
 **0**にマージ アーティクルへの変更はスナップショットが無効であることがありません。  
  
 **1**マージ アーティクルへの変更は、スナップショットが無効であることで発生する可能性がありますを指定します。 場合、値がある場合と**1** 、新しいスナップショットを作成する権限が与えられます。  
  
 [* *@force_reinit_subscription =] * * * 更によって*  
 サブスクリプションを再初期化する機能を有効または無効にします。 *更によって*は bit で、既定値は**0**します。  
  
 **0**マージ アーティクルへの変更では、サブスクリプションを再初期化するのには発生しませんを指定します。  
  
 **1**マージ アーティクルへの変更は、再初期化されるサブスクリプションで発生する可能性がありますを指定します。 場合、値がある場合と**1**のサブスクリプションの再初期化を許可します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_mergearticlecolumn**はマージ レプリケーションで使用します。  
  
 自動 ID 範囲管理が使用されている場合、アーティクルから ID 列を削除することはできません。 詳細については、「[Replicate Identity Columns](../../relational-databases/replication/publish/replicate-identity-columns.md)」 (ID 列のレプリケート) を参照してください。  
  
 最初のスナップショットが作成された後、アプリケーションで新しく列方向のパーティションを設定する場合は、新しいスナップショットを作成して各サブスクリプションに再適用する必要があります。 スナップショットは、次回スケジュールされているスナップショット エージェントおよびディストリビューション エージェント、またはマージ エージェントが実行されるときに適用されます。  
  
 行レベルの追跡を使用して競合を検出する場合 (既定値)、ベース テーブルには最大 1,024 列含めることができますが、最大 246 列がパブリッシュされるようにアーティクルから列をフィルター選択する必要があります。 列の追跡を使用する場合、ベース テーブルには最大 246 列を含めることができます。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_AddMergeArticle](../../relational-databases/replication/codesnippet/tsql/sp-mergearticlecolumn-tr_1.sql)]  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_mergearticlecolumn**します。  
  
## <a name="see-also"></a>参照  
 [マージ アーティクル間の結合フィルターの定義および変更](../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md)   
 [マージ アーティクルのパラメーター化された行フィルターの定義および変更](../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)   
 [パブリッシュされたデータのフィルター処理](../../relational-databases/replication/publish/filter-published-data.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
