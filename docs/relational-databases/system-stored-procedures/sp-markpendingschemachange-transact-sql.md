---
title: "sp_markpendingschemachange (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sp_markpendingschemachange
- sp_markpendingschemachange_TSQL
helpviewer_keywords: sp_markpendingschemachange
ms.assetid: 01100309-7bef-4154-85bf-f18489577e37
caps.latest.revision: "12"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fc1712e646a8efda1fdc4f06d912a1021a0beaff
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spmarkpendingschemachange-transact-sql"></a>sp_markpendingschemachange (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  選択した保留中のスキーマ変更がレプリケートされないように、管理者がそのスキーマ変更をスキップできるようにします。これは、マージ パブリケーションをサポートするための操作です。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
> [!CAUTION]  
>  このストアド プロシージャによって、スキーマ変更がレプリケートされなくなる可能性があります。 このストアド プロシージャを使用して問題を解決するのは、再初期化などの他の手段を既に試した場合、またはそれらの手段によるパフォーマンスのコストが高すぎる場合に限定してください。  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_markpendingschemachange [@publication = ] 'publication'  
    [ , [ @schemaversion = ] schemaversion ]  
    [ , [ @status = ] 'status' ]  
```  
  
## <a name="arguments"></a>引数  
 [**@publication=** ] **'***パブリケーション***'**  
 パブリケーションの名前です。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [  **@schemaversion=** ] *schemaversion*  
 保留中のスキーマ変更を指定します。 *schemaversion*は**int**、既定値は**0**します。 使用して[sp_enumeratependingschemachanges (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-enumeratependingschemachanges-transact-sql.md)パブリケーションの保留中のスキーマ変更を一覧表示します。  
  
 [  **@status=** ] **'***ステータス***'**  
 保留中のスキーマ変更をスキップするかどうかを指定します。 *ステータス*は**nvarchar (10)**で、既定値は**active**です。 場合の値*ステータス*は**スキップ**、選択したスキーマの変更はレプリケートされません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_markpendingschemachange**はマージ レプリケーションで使用します。  
  
 **sp_markpendingschemachange**はストアド プロシージャは、マージ レプリケーションのサポートのためのものし、再初期化などの他の解決策状況の修正に失敗したかで高価すぎる場合にのみ使用する必要がありますパフォーマンスの条件。  
  
## <a name="permissions"></a>Permissions  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_markpendingschemachange**です。  
  
## <a name="see-also"></a>参照  
 [sysmergeschemachange &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/sysmergeschemachange-transact-sql.md)  
  
  
