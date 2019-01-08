---
title: sp_copysnapshot (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_copysnapshot
- sp_copysnapshot_TSQL
helpviewer_keywords:
- sp_copysnapshot
ms.assetid: a012a32f-6f26-45bf-8046-b51cd7fec455
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0cb4757d454343b48d5eea74d10d66cdbaa7a52a
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52817194"
---
# <a name="spcopysnapshot-transact-sql"></a>sp_copysnapshot (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  表示されているフォルダーに、指定されたパブリケーションのスナップショット フォルダーをコピー、  **@destination_folder**します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。 このストアド プロシージャは、スナップショットを CD-ROM などのリムーバブル メディアにコピーするときに効果的です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_copysnapshot [ @publication = ] 'publication', [ @destination_folder = ] 'destination_folder' ]  
    [ , [ @subscriber = ] 'subscriber' ]  
    [ , [ @subscriber_db = ] 'subscriber_db' ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@publication=**] **'***publication***'**  
 スナップショットの内容をコピーするパブリケーションの名前を指定します。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [  **@destination_folder=**] **'***destination_folder***'**  
 パブリケーションのスナップショットの内容をコピーするフォルダーの名前です。 *destination_folder*は**nvarchar (255)**、既定値はありません。 *Destination_folder*別の場所などの別のサーバー、ネットワーク ドライブ、またはリムーバブル メディア (Cd-rom やリムーバブル ディスク) を指定できます。  
  
 [  **@subscriber=**] **'***サブスクライバー***'**  
 サブスクライバーの名前です。 *サブスクライバー*が sysname で、既定値は NULL です。  
  
 [  **@subscriber_db=**] **'***@subscriber_db***'**  
 サブスクリプション データベースの名前です。 *@subscriber_db*が sysname で、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_copysnapshot**はあらゆる種類のレプリケーションで使用します。 実行しているサブスクライバー [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 7.0 以前は、代替スナップショットの場所を使用できません。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_copysnapshot**します。  
  
## <a name="see-also"></a>参照  
 [スナップショット フォルダーの代替位置](../../relational-databases/replication/alternate-snapshot-folder-locations.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
