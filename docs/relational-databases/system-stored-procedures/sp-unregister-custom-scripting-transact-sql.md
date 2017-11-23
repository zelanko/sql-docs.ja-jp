---
title: "sp_unregister_custom_scripting (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sp_unregister_custom_scripting_TSQL
- sp_unregister_custom_scripting
helpviewer_keywords: sp_unregister_custom_scripting
ms.assetid: b6e9e0d2-9144-434d-88af-4874f2582399
caps.latest.revision: "26"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fce6b2d16e732b76519cb0fbf66a16ca5db6928f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spunregistercustomscripting-transact-sql"></a>sp_unregister_custom_scripting (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  このストアド プロシージャは、ユーザー定義カスタム ストアド プロシージャを削除または[!INCLUDE[tsql](../../includes/tsql-md.md)]スクリプト ファイルを実行して登録された[sp_register_custom_scripting](../../relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql.md)です。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_unregister_custom_scripting [ @type  = ] 'type'  
    [ , [ @publication = ] 'publication' ]  
    [ , [ @article = ] 'article' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@type**  =] **'***型***'**  
 削除するカスタム ストアド プロシージャまたはスクリプトの種類を指定します。 *型*は**varchar (16)**, で、既定値はありませんは、次の値のいずれかを指定します。  
  
|値|Description|  
|-----------|-----------------|  
|**挿入します。**|登録したカスタム ストアド プロシージャまたはスクリプトを、INSERT ステートメントがレプリケートされるときに実行。|  
|**更新プログラム**|登録したカスタム ストアド プロシージャまたはスクリプトを、UPDATE ステートメントがレプリケートされるときに実行。|  
|**削除**|登録したカスタム ストアド プロシージャまたはスクリプトを、DELETE ステートメントがレプリケートされるときに実行。|  
|**custom_script**|登録したカスタム ストアド プロシージャまたはスクリプトを、データ定義言語 (DDL) トリガーの最後に実行。|  
  
 [  **@publication**  =] **'***パブリケーション***'**  
 カスタム ストアド プロシージャまたはスクリプトを削除するパブリケーションの名前を指定します。 *パブリケーション*は**sysname**、既定値は NULL です。  
  
 [  **@article**  =] **'***記事***'**  
 カスタム ストアド プロシージャまたはスクリプトを削除するアーティクルの名前を指定します。 *記事*は**sysname**、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_unregister_custom_scripting**は、スナップショットおよびトランザクション レプリケーションで使用します。  
  
## <a name="permissions"></a>Permissions  
 メンバーにのみ、 **sysadmin**固定サーバー ロール、 **db_owner**固定データベース ロール、または**db_ddladmin**固定データベース ロールが実行できる**sp _unregister_custom_scripting**です。  
  
## <a name="see-also"></a>参照  
 [sp_register_custom_scripting &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql.md)  
  
  
