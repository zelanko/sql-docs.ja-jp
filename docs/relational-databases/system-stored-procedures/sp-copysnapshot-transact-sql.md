---
title: "sp_copysnapshot (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
- sp_copysnapshot
- sp_copysnapshot_TSQL
helpviewer_keywords: sp_copysnapshot
ms.assetid: a012a32f-6f26-45bf-8046-b51cd7fec455
caps.latest.revision: "20"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fa61d1c75b74a1ac64f3462d35e52d6023806f7a
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spcopysnapshot-transact-sql"></a>sp_copysnapshot (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  表示されるフォルダーに、指定されたパブリケーションのスナップショット フォルダーをコピー、  **@destination_folder**です。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。 このストアド プロシージャは、スナップショットを CD-ROM などのリムーバブル メディアにコピーするときに効果的です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_copysnapshot [ @publication = ] 'publication', [ @destination_folder = ] 'destination_folder' ]  
    [ , [ @subscriber = ] 'subscriber' ]  
    [ , [ @subscriber_db = ] 'subscriber_db' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@publication=**] **'***パブリケーション***'**  
 スナップショットの内容をコピーするパブリケーションの名前を指定します。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [  **@destination_folder=**] **'***destination_folder***'**  
 パブリケーションのスナップショットの内容がコピーされるフォルダーの名前です。 *destination_folder*は**nvarchar (255)**、既定値はありません。 *Destination_folder*別の場所など、別のサーバー、ネットワーク ドライブ、またはリムーバブル メディア (Cd-rom やリムーバブル ディスク) などを指定できます。  
  
 [  **@subscriber=**] **'***サブスクライバー***'**  
 サブスクライバーの名前です。 *サブスクライバー*は sysname で、既定値は NULL です。  
  
 [  **@subscriber_db=**] **'***@subscriber_db***'**  
 サブスクリプション データベースの名前です。 *@subscriber_db*は sysname で、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_copysnapshot**はあらゆる種類のレプリケーションで使用します。 実行しているサブスクライバー [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 7.0 以前はスナップショットの代替位置を使用することはできません。  
  
## <a name="permissions"></a>Permissions  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_copysnapshot**です。  
  
## <a name="see-also"></a>参照  
 [スナップショット フォルダーの代替位置](../../relational-databases/replication/alternate-snapshot-folder-locations.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
