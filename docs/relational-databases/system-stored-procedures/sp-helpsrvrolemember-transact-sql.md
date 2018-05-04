---
title: sp_helpsrvrolemember (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_helpsrvrolemember
- sp_helpsrvrolemember_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpsrvrolemember
ms.assetid: d0714913-8d6b-4de3-b042-3ae9934f839d
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 76dd3316c5b2f3636bd0155bb29f5fad2d0fbeef
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sphelpsrvrolemember-transact-sql"></a>sp_helpsrvrolemember (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 固定サーバー ロールのメンバーに関する情報を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helpsrvrolemember [ [ @srvrolename = ] 'role' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@srvrolename =** ] **'***ロール***'**  
 固定サーバー ロールの名前です。 *ロール*は**sysname**、既定値は NULL です。 場合*ロール*が指定されていない、結果セットには、すべての固定サーバー ロールに関する情報が含まれています。  
  
 *ロール*値は次のいずれかを指定できます。  
  
|固定サーバー ロール|Description|  
|-----------------------|-----------------|  
|sysadmin|システム管理者。|  
|securityadmin|セキュリティ管理者。|  
|serveradmin|サーバー管理者。|  
|setupadmin|セットアップ管理者。|  
|processadmin|プロセス管理者。|  
|diskadmin|ディスク管理者。|  
|dbcreator|データベース作成者。|  
|bulkadmin|BULK INSERT ステートメントを実行できます。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|ServerRole|**sysname**|サーバー ロールの名前。|  
|MemberName|**sysname**|サーバー ロールのメンバーの名前|  
|MemberSID|**varbinary(85)**|メンバー名のセキュリティ識別子|  
  
## <a name="remarks"></a>解説  
 Sp_helprolemember を使用して、データベース ロールのメンバーを表示します。  
  
 すべてのログインは、public のメンバーです。 sp_helpsrvrolemember が public ロールを認識していないため、内部的には、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリック ロールとして実装しません。  
  
 追加するサーバーの役割から削除されたメンバーを参照してくださいまたは[ALTER SERVER ROLE &#40;TRANSACT-SQL&#41;](../../t-sql/statements/alter-server-role-transact-sql.md)です。  
  
 sp_helpsrvrolemember には、引数としてユーザー定義サーバー ロールはなりません。 ユーザー定義サーバー ロールのメンバーを調べるには、例を参照してください。 [ALTER SERVER ROLE &#40;TRANSACT-SQL&#41;](../../t-sql/statements/alter-server-role-transact-sql.md)です。  
  
## <a name="permissions"></a>権限  
 public ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例のメンバーを一覧表示、`sysadmin`固定サーバー ロール。  
  
```  
EXEC sp_helpsrvrolemember 'sysadmin';  
```  
  
## <a name="see-also"></a>参照  
 [sp_helprole &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helprole-transact-sql.md)   
 [sp_helprolemember &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helprolemember-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [セキュリティ ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [セキュリティ関数 &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
  
  
