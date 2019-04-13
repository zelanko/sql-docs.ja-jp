---
title: sp_audit_write (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_audit_write
- sp_audit_write_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_audit_write
ms.assetid: 4c523848-1ce6-49ad-92b3-e0e90f24f1c2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 450b1cdde9185edee5eac41f52d209e43a7ae22f
ms.sourcegitcommit: acb5de9f493238180d13baa302552fdcc30d83c0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59542162"
---
# <a name="spauditwrite-transact-sql"></a>sp_audit_write (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  ユーザー定義の監査イベントを追加、 **USER_DEFINED_AUDIT_GROUP**します。 場合**USER_DEFINED_AUDIT_GROUP**が有効でない**sp_audit_write**は無視されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
sp_audit_write [ @user_defined_event_id = ] user_defined_event_id
    [ , [ @succeeded = ] succeeded ]
    [ , [ @user_defined_information = ] 'user_defined_information' ]
    [ ; ]
```  
  
## <a name="arguments"></a>引数  
 `[ @user_defined_event_id = ] user_defined_event_id`  
 パラメーターがユーザーによって定義されに記録、 **user_defined_event_id**監査ログの列。 *@user_defined_event_id* 型は、 **smallint**します。  
  
 `[ @succeeded = ] succeeded`  
 イベントが正常に終了したかどうかを示すためにユーザーによって渡されるパラメーター。 これは、監査ログの成功の列に表示されます。 `@succeeded` **ビット**します。  
  
 `[ @user_defined_information = ] 'user_defined_information'`  
 ユーザーによって定義され、監査ログの新しい user_defined_event_id 列に記録されるテキストです。 `@user_defined_information` **nvarchar (4000)** します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
 失敗の原因となるのは、正しくない入力パラメーターや、監査ログへの書き込みのエラーです。  
  
## <a name="remarks"></a>コメント  
 ときに、 **USER_DEFINED_AUDIT_GROUP**サーバー監査の仕様またはデータベース監査の仕様、によってトリガーされるイベントのいずれかに追加されます**sp_audit_write**は監査ログに含まれます。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーシップが必要です、**パブリック**データベース ロール。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-creating-a-user-defined-audit-event-with-informational-text"></a>A. 情報テキストを含むユーザー定義の監査イベントを作成します。  
 次の例では、監査イベントを id が 27、成功時の値が 0 であり、含まれるオプションの情報テキストを作成します。  
  
```  
EXEC sp_audit_write @user_defined_event_id =  27 ,   
              @succeeded =  0   
            , @user_defined_information = N'Access to a monitored object.' ;  
```  
  
### <a name="b--creating-a-user-defined-audit-event-without-informational-text"></a>B.  ユーザー定義の監査イベントを情報テキストなしで作成する  
 次の例では、ID が 27、成功時の値が 0 で、オプションの情報テキストまたはオプションのパラメーター名を含まない監査イベントを作成します。  
  
```  
EXEC sp_audit_write 27, 0;  
  
```  
  
## <a name="see-also"></a>参照  
 [セキュリティ ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sys.server_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [sp_addrole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrole-transact-sql.md)   
 [CREATE USER &#40;Transact-SQL&#41;](../../t-sql/statements/create-user-transact-sql.md)   
 [sp_dropuser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropuser-transact-sql.md)   
 [sp_grantdbaccess &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantdbaccess-transact-sql.md)   
 [sp_grantlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
