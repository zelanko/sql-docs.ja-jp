---
title: "sp_changeobjectowner (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_changeobjectowner_TSQL
- sp_changeobjectowner
dev_langs: TSQL
helpviewer_keywords: sp_changeobjectowner
ms.assetid: 45b3dc1c-1cde-45b7-a248-5195c12973e9
caps.latest.revision: "37"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: ac7463bd6564a07a86e25d4e7a643fbe0c2e0725
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spchangeobjectowner-transact-sql"></a>sp_changeobjectowner (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在のデータベース内のオブジェクトの所有者を変更します。  
  
> [!IMPORTANT]  
>  このストアド プロシージャで使用可能なオブジェクトでのみ動作[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]です。 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]使用して[ALTER SCHEMA](../../t-sql/statements/alter-schema-transact-sql.md)または[ALTER AUTHORIZATION](../../t-sql/statements/alter-authorization-transact-sql.md)代わりにします。 **sp_changeobjectowner**スキーマと所有者の両方を変更します。 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] との互換性を維持するために、現在の所有者と新しい所有者がデータベースのユーザー名と同じ名前のスキーマを所有している場合は、このストアド プロシージャはオブジェクトの所有者だけを変更します。  
  
> [!IMPORTANT]  
>  このストアド プロシージャには、新しい権限要件が追加されています。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_changeobjectowner [ @objname = ] 'object' , [ @newowner = ] 'owner'  
```  
  
## <a name="arguments"></a>引数  
 [  **@objname =** ] **'***オブジェクト***'**  
 現在のデータベース内の既存のテーブル、ビュー、ユーザー定義関数、またはストアド プロシージャの名前です。 *オブジェクト*は、 **nvarchar (776)**、既定値はありません。 *オブジェクト*形式で、既存のオブジェクトの所有者で修飾できます*existing_owner***.***オブジェクト*スキーマとその所有者の名前が同じ場合です。  
  
 [  **@newowner=**] **'***所有者* **'**  
 オブジェクトの新しい所有者となるセキュリティ アカウントの名前です。 *所有者*は**sysname**、既定値はありません。 *所有者*有効なデータベース ユーザー、サーバーの役割をする必要があります[!INCLUDE[msCoName](../../includes/msconame-md.md)]Windows ログイン、または現在のデータベースへのアクセスを持つ Windows グループです。 新しい所有者が、対応するデータベース レベルのプリンシパルを与えられていない Windows ユーザーまたは Windows グループである場合、データベース ユーザーが作成されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_changeobjectowner**オブジェクトからすべての既存のアクセス許可を削除します。 実行後も保持するすべてのアクセス許可を再適用する必要が**sp_changeobjectowner**です。 したがってをお勧めを既存の権限を実行する前にスクリプトを**sp_changeobjectowner**です。 オブジェクトの所有権を変更した後で、そのスクリプトを使用して権限を再適用できます。 権限スクリプトを実行する前に、そのスクリプトでオブジェクトの所有者を変更する必要があります。  
  
 セキュリティ保護可能なオブジェクトの所有者を変更するには、ALTER AUTHORIZATION を使用します。 スキーマを変更するには、ALTER SCHEMA を使用します。  
  
## <a name="permissions"></a>Permissions  
 メンバーシップが必要、 **db_owner**両方の固定データベース ロールのメンバーシップまたは、 **db_ddladmin**固定データベース ロールおよび**db_securityadmin**固定データベース ロールオブジェクトに対する CONTROL 権限もします。  
  
## <a name="examples"></a>使用例  
 次の例では、`authors` テーブルの所有者を `Corporate\GeorgeW` に変更します。  
  
```  
EXEC sp_changeobjectowner 'authors', 'Corporate\GeorgeW';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [ALTER SCHEMA &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-schema-transact-sql.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [ALTER AUTHORIZATION &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [sp_changedbowner &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-changedbowner-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
