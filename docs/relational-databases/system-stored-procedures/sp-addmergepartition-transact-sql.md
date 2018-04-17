---
title: sp_addmergepartition (TRANSACT-SQL) |Microsoft ドキュメント
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
- sp_addmergepartition
- sp_addmergepartition_TSQL
helpviewer_keywords:
- sp_addmergepartition
ms.assetid: 02a5f46b-e5ff-4932-a3ff-7f0fd82d0981
caps.latest.revision: 31
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a169b85f0ae207f72ba0f142633aa323403745c3
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="spaddmergepartition-transact-sql"></a>sp_addmergepartition (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  値でフィルター処理されるサブスクリプションに対して動的にフィルター選択されたパーティションを作成[HOST_NAME](../../t-sql/functions/host-name-transact-sql.md)または[SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md)サブスクライバーです。 このストアド プロシージャは、パブリッシュされるデータベース上のパブリッシャー側で実行されるもので、手動でパーティションを生成する場合に使用します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_addmergepartition [ @publication = ] 'publication'  
        , [ @suser_sname = ] 'suser_sname'  
        , [ @host_name = ] 'host_name'  
```  
  
## <a name="arguments"></a>引数  
 [ **@publication**=] **'***パブリケーション***'**  
 パーティションが作成されるマージ パブリケーションを指定します。 *パブリケーション*は**sysname**、既定値はありません。 場合*suser_sname*指定するの値*hostname* NULL にする必要があります。  
  
 [ **@suser_sname**=] **'***suser_sname***'**  
 値によってフィルター選択は、サブスクリプションのパーティションを作成するときに使用される値は、 [SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md)サブスクライバーでの関数。 *suser_sname*は**sysname**、既定値はありません。  
  
 [ **@host_name**=] **'***host_name***'**  
 値によってフィルター選択は、サブスクリプションのパーティションを作成するときに使用される値は、 [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md)サブスクライバーでの関数。 *host_name*は**sysname**、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_addmergepartition**はマージ レプリケーションで使用します。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_MergeDynamicPubPlusPartition](../../relational-databases/replication/codesnippet/tsql/sp-addmergepartition-tra_1.sql)]  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_addmergepartition**です。  
  
## <a name="see-also"></a>参照  
 [パラメーター化されたフィルターによるマージ パブリケーションのスナップショットを作成します。](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)   
 [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)  
  
  
