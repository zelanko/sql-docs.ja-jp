---
title: "sp_addmergefilter (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
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
- sp_addmergefilter
- sp_addmergefilter_TSQL
helpviewer_keywords:
- sp_addmergefilter
ms.assetid: 4c118cb1-2008-44e2-a797-34b7dc34d6b1
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bae5cbac50c347247bba5b0488a7fb70ad8e71a3
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spaddmergefilter-transact-sql"></a>sp_addmergefilter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  別のテーブルとの結合に基づいてパーティションを作成するために、新しいマージ フィルターを追加します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_addmergefilter [ @publication = ] 'publication'   
        , [ @article = ] 'article'   
        , [ @filtername = ] 'filtername'   
        , [ @join_articlename = ] 'join_articlename'   
        , [ @join_filterclause = ] join_filterclause  
    [ , [ @join_unique_key = ] join_unique_key ]  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
    [ , [ @filter_type = ] filter_type ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@publication=** ] **'***パブリケーション***'**  
 マージ フィルターを追加するパブリケーションの名前です。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [  **@article=** ] **'***記事***'**  
 マージ フィルターを追加するアーティクルの名前です。 *記事*は**sysname**、既定値はありません。  
  
 [  **@filtername=** ] **'***filtername***'**  
 フィルターの名前です。 *filtername*必須パラメーターです。 *filtername*は**sysname**、既定値はありません。  
  
 [  **@join_articlename=** ] **'***join_articlename***'**  
 子アーティクルがで指定された親アーティクルです*記事*で指定された結合句を使用して結合する必要があります*join_filterclause*を満たす子アーティクル内の行を判別するために、マージ フィルターのフィルター条件です。 *join_articlename*は**sysname**、既定値はありません。 指定されたパブリケーションでアーティクルがある必要があります*パブリケーション*です。  
  
 [  **@join_filterclause=** ] *join_filterclause*  
 指定された子アーティクルを結合に使用する必要がある join 句は、*記事*とで指定された親アーティクル*join_article*、マージ フィルターの条件を満たす行を判断するためです。 *join_filterclause*は**nvarchar (1000)**です。  
  
 [  **@join_unique_key=** ] *join_unique_key*  
 場合の指定子アーティクル間の結合*記事*と親アーティクル*join_article*は一対多、一対一、多対一または多対多です。 *join_unique_key*は**int**、既定値は 0 です。 **0**多対一または多対多の結合を示します。 **1**一対一または一対多の結合を示します。 この値は**1**結合列に一意のキーで構成される場合*join_article*、または*join_filterclause*間の外部キーは*記事*との主キー *join_article*です。  
  
> [!CAUTION]  
>  このパラメーターにのみ設定**1**一意性を保証する親アーティクルの基になるテーブルに結合する列に制約がある場合。 場合*join_unique_key*に設定されている**1**正しく、データの未集約が発生するされません。  
  
 [  **@force_invalidate_snapshot=** ]*更によって*  
 このストアド プロシージャが実行する操作によって既存のスナップショットが無効になることを許可します。 *更によって*は、**ビット**、既定で**0**します。  
  
 **0**マージ アーティクルへの変更は、スナップショットが無効であることをされませんを指定します。 ストアド プロシージャが、変更は、新しいスナップショット必要になることを検出した場合、エラーが発生し、変更は行われません。  
  
 **1**マージ アーティクルへの変更はスナップショットが無効であることがあり、新しいスナップショットが必要となる既存のサブスクリプションがある場合は、アクセス許可を与える不使用とマークするのには、既存のスナップショットと、新しいスナップショットを指定します生成されます。  
  
 [  **@force_reinit_subscription=** ]*更によって*  
 このストアド プロシージャが実行する操作によって、既存のサブスクリプションの再初期化が必要になることを許可します。 *更によって*は、**ビット**、既定値は 0 です。  
  
 **0**マージ アーティクルへの変更では、サブスクリプションを再初期化するのには発生しませんを指定します。 変更にサブスクリプションの再初期化が必要であることをストアド プロシージャが検出すると、エラーが発生し、変更は加えられません。  
  
 **1**マージ アーティクルへの変更が初期化されることを既存のサブスクリプションを再発生するサブスクリプションを再初期化を許可します。  
  
 [  **@filter_type=** ] *filter_type*  
 追加されるフィルターの型を指定します。 *filter_type*は**tinyint**値は次のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|結合フィルターのみです。 [!INCLUDE[ssEW](../../includes/ssew-md.md)] のサブスクライバーをサポートするために必要です。|  
|**2**|論理レコード リレーションシップのみです。|  
|**3**|結合フィルターおよび論理レコード リレーションシップの両方です。|  
  
 詳細については、「[Group Changes to Related Rows with Logical Records](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md)」 (論理レコードによる関連行への変更のグループ化) を参照してください。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_addmergefilter**はマージ レプリケーションで使用します。  
  
 **sp_addmergefilter**テーブル アーティクルにのみ使用できます。 ビュー アーティクルおよびインデックス付きビュー アーティクルはサポートされません。  
  
 このプロシージャは、(結合フィルターを持つ場合でも持たない場合でも) 2 つのアーティクルの間に論理リレーションシップを追加するために使用できます。 *filter_type*かどうか追加されるマージ フィルターは結合フィルター、論理リレーション、またはその両方を指定するために使用します。  
  
 論理レコードを使用するには、パブリケーションとアーティクルが多くの要件を満たしている必要があります。 詳細については、「[Group Changes to Related Rows with Logical Records](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md)」 (論理レコードによる関連行への変更のグループ化) を参照してください。  
  
 通常、パブリッシュされている主キー テーブルを参照する外部キーを持ち、その主キーがそのアーティクルで定義されたフィルターを持つようなアーティクルに対してこのオプションを使用します。 主キー行のサブセットを使用して、サブスクライバーにレプリケートする外部キー行を規定します。  
  
 2 つのパブリッシュされたアーティクルのコピー元のテーブルが同じテーブル オブジェクト名を共有している場合は、2 つのアーティクルの間に結合フィルターを追加することはできません。 このような場合、それぞれのテーブルを所有するスキーマが異なっていて、それぞれが一意のアーティクル名を持っていても、結合フィルターの作成は失敗します。  
  
 パラメーター化された行フィルターと結合フィルターの両方がテーブル アーティクル上で使用される場合、レプリケーションでは、サブスクライバーのパーティション内に行があるかどうかを判別します。 これは、結合フィルターまたはフィルター処理関数のいずれかの評価によって (を使用して、 [OR](../../t-sql/language-elements/or-transact-sql.md)演算子)、2 つの条件の交差部分を評価するのではなく (を使用して、 [AND](../../t-sql/language-elements/and-transact-sql.md)演算子)。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_addmergefilter](../../relational-databases/replication/codesnippet/tsql/sp-addmergefilter-transa_1.sql)]  
  
## <a name="permissions"></a>Permissions  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_addmergefilter**です。  
  
## <a name="see-also"></a>参照  
 [Define an Article](../../relational-databases/replication/publish/define-an-article.md)   
 [マージ アーティクル間の結合フィルター定義および変更](../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md)   
 [結合フィルター](../../relational-databases/replication/merge/join-filters.md)   
 [sp_changemergefilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changemergefilter-transact-sql.md)   
 [sp_dropmergefilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dropmergefilter-transact-sql.md)   
 [sp_helpmergefilter &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helpmergefilter-transact-sql.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
