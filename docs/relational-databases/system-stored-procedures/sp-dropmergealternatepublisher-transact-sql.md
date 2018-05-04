---
title: sp_dropmergealternatepublisher (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/03/2017
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
- sp_dropmergealternatepublisher
- sp_dropmergealternatepublisher_TSQL
helpviewer_keywords:
- sp_dropmergealternatepublisher
ms.assetid: a7dee4e2-2a60-41da-9d1d-6f991d7e2c5e
caps.latest.revision: 29
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 4ab888dd5722e4f5fadb6301fa89377bbc5fe16e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spdropmergealternatepublisher-transact-sql"></a>sp_dropmergealternatepublisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  代替のパブリッシャーをマージ パブリケーションから削除します。 このストアド プロシージャは、サブスクライバー側でサブスクリプション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_dropmergealaternatepublisher [ @publisher = ] 'publisher'    , [ @publisher_db = ] 'publisher_db'    , [ @publication = ] 'publication'    , [ @alternate_publisher = ] 'alternate_publisher'    , [ @alternate_publisher_db = ] 'alternate_publisher_db'    , [ @alternate_publication = ] 'alternate_publication'  
```  
  
## <a name="arguments"></a>引数  
 [ **@publisher=**] **'***publisher***'**  
 現在のパブリッシャーの名前を指定します。 *パブリッシャー*は**sysname**、既定値はありません。  
  
 [ **@publisher_db=**] **'***publisher_db***'**  
 現在のパブリケーション データベースの名前を指定します。 *publisher_db*は**sysname**、既定値はありません。  
  
 [  **@publication =**] **'***パブリケーション***'**  
 現在のパブリケーションの名前を指定します。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [  **@alternate_publisher=**] **'***alternate_publisher***'**  
 代替同期パートナーとして削除する代替パブリッシャーの名前を指定します。 *alternate_publisher*は**sysname**、既定値はありません。  
  
 [  **@alternate_publisher_db=**] **'***alternate_publisher_db***'**  
 代替同期パートナー パブリケーション データベースとして削除するパブリケーション データベースの名前を指定します。 *alternate_publisher_db*は**sysname**、既定値はありません。  
  
 [  **@alternate_publication=**] **'***alternate_publication***'**  
 代替同期パートナー パブリケーションとして削除するパブリケーションの名前を指定します。 *alternate_publication*は**sysname**、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_dropmergealternatepublisher**はマージ レプリケーションで使用します。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_dropmergelternatepublisher**です。  
  
## <a name="see-also"></a>参照  
 [sp_addmergealternatepublisher &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergealternatepublisher-transact-sql.md)  
  
  
