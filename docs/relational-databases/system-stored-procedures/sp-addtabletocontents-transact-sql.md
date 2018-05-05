---
title: sp_addtabletocontents (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/04/2017
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
- sp_addtabletocontents_TSQL
- sp_addtabletocontents
helpviewer_keywords:
- sp_addtabletocontents
ms.assetid: 2ea27001-74f4-463e-bf1b-b6b5a86b9219
caps.latest.revision: 23
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: a8302f6e016571030a978bfe98bb301b810c949f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spaddtabletocontents-transact-sql"></a>sp_addtabletocontents (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在追跡テーブルに含まれていないソース テーブル内の行への参照をマージ追跡テーブルに挿入します。 このオプションを使用する一括で読み込んだ大量のデータを使用して**bcp**、マージ追跡トリガーを起動しません。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_addtabletocontents [ @table_name = ] 'table_name'  
    [ , [ @owner_name = ] 'owner_name' ]  
    [ , [ @filter_clause = ] 'filter_clause' ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@table_name=**] **'***table_name***'**  
 テーブルの名前を指定します。 *table_name*は**sysname**、既定値はありません。  
  
 [  **@owner_name=**] **'***owner_name***'**  
 テーブルの所有者の名前を指定します。 *owner_name*は**sysname**、既定値は NULL です。  
  
 [  **@filter_clause=** ] **'***filter_clause***'**  
 新たに読み込まれたデータのうち、どの行をマージ追跡テーブルに追加するかを制御するフィルター句を指定します。 *filter_clause*は**nvarchar (4000)** 既定値は NULL です。 場合*filter_clause*は**null**、すべての一括が読み込まれた行が追加されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_addtabletocontents**はマージ レプリケーションでのみ使用します。  
  
 内の行、 *table_name*によって参照される、 **rowguidcol**され、参照がマージ追跡テーブルに追加されます。 **sp_addtabletocontents**一括マージ レプリケーションを使用してパブリッシュされるテーブルにデータをコピーした後に使用する必要があります。 このストアド プロシージャは、コピーされた行のトラッキングを実行し、次の同期処理の際に新しい行を確実に挿入します。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_addtabletocontents**です。  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
