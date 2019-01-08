---
title: sp_markpendingschemachange (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_markpendingschemachange
- sp_markpendingschemachange_TSQL
helpviewer_keywords:
- sp_markpendingschemachange
ms.assetid: 01100309-7bef-4154-85bf-f18489577e37
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ba9320a155ca0af5750ca66cf10564227a3197d3
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52818814"
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
 保留中のスキーマ変更を指定します。 *schemaversion*は**int**の既定値を持つ**0**します。 使用[sp_enumeratependingschemachanges &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-enumeratependingschemachanges-transact-sql.md) 、パブリケーションの保留中のスキーマ変更を一覧表示します。  
  
 [  **@status=** ] **'***状態***'**  
 保留中のスキーマ変更をスキップするかどうかを指定します。 *ステータス*は**nvarchar (10)** の既定値を持つ**active**します。 場合の値*状態*は**スキップ**、選択したスキーマの変更はレプリケートされません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_markpendingschemachange**はマージ レプリケーションで使用します。  
  
 **sp_markpendingschemachange**はストアド プロシージャは、マージ レプリケーションのサポートのためのものし、再初期化などの他の修正操作状況の修正に失敗したかがでコストが高すぎる場合にのみ使用する必要がありますパフォーマンスの条件。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_markpendingschemachange**します。  
  
## <a name="see-also"></a>参照  
 [sysmergeschemachange &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/sysmergeschemachange-transact-sql.md)  
  
  
