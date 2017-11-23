---
title: "sp_deletemergeconflictrow (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_deletemergeconflictrow
- sp_deletemergeconflictrow_TSQL
helpviewer_keywords: sp_deletemergeconflictrow
ms.assetid: 64cf1186-28b8-4cd9-88f1-a7808a9c8d60
caps.latest.revision: "26"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e085a7010f25f40b95a45d8ddd0c7b455d7266c6
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spdeletemergeconflictrow-transact-sql"></a>sp_deletemergeconflictrow (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  競合テーブルから行を削除または[MSmerge_conflicts_info (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/msmerge-conflicts-info-transact-sql.md)テーブル。 このストアド プロシージャは、競合テーブルが格納されているコンピューターの、任意のデータベース上で実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_deletemergeconflictrow [ [ @conflict_table = ] 'conflict_table' ]  
    [ , [ @source_object = ] 'source_object' ]  
    { , [ @rowguid = ] 'rowguid'  
        , [ @origin_datasource = ] 'origin_datasource' ] }  
    [ , [ @drop_table_if_empty = ] 'drop_table_if_empty' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@conflict_table=**] **'***conflict_table***'**  
 競合テーブルの名前を指定します。 *conflict_table*は**sysname**、既定値は **%**です。 場合、 *conflict_table*は NULL として指定または **%** 、競合は、削除の競合と一致する行であると見なされます*rowguid*と*origin_datasource*と*source_object*から削除されて、 [MSmerge_conflicts_info (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/msmerge-conflicts-info-transact-sql.md)テーブル。  
  
 [  **@source_object=**] **'***source_object***'**  
 ソース テーブルの名前です。 *source_object*は**nvarchar (386)**、既定値は NULL です。  
  
 [  **@rowguid =**] **'***rowguid***'**  
 削除競合の行識別子 (ROWID) を指定します。 *rowguid*は**uniqueidentifier**、既定値はありません。  
  
 [  **@origin_datasource=**] **'***origin_datasource***'**  
 競合の元を指定します。 *origin_datasource*は**varchar (255)**、既定値はありません。  
  
 [  **@drop_table_if_empty=**] **'***drop_table_if_empty***'**  
 示すフラグです、 *conflict_table*は場合に削除するのには空です。 *drop_table_if_empty*は**varchar (10)**、既定値は FALSE。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_deletemergeconflictrow**はマージ レプリケーションで使用します。  
  
 [MSmerge_conflicts_info &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/msmerge-conflicts-info-transact-sql.md)テーブルはシステム テーブルであり、空である場合でも、データベースからは削除されません。  
  
## <a name="permissions"></a>Permissions  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_deletemergeconflictrow**です。  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
