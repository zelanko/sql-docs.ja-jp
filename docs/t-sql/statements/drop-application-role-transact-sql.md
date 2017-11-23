---
title: "アプリケーション ロールを削除 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP_APPLICATION_ROLE_TSQL
- DROP APPLICATION ROLE
dev_langs: TSQL
helpviewer_keywords:
- dropping application roles
- deleting application roles
- removing application roles
- application roles [SQL Server], removing
- DROP APPLICATION ROLE statement
ms.assetid: 44121ee7-ef40-405d-b03b-f8ddb4e3c559
caps.latest.revision: "24"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 05cac03b57e3bb51086b7f97c6a9feb1f7c7a091
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="drop-application-role-transact-sql"></a>DROP APPLICATION ROLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  アプリケーション ロールを現在のデータベースから削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
DROP APPLICATION ROLE rolename  
```  
  
## <a name="arguments"></a>引数  
 *rolename*  
 削除するアプリケーション ロールの名前を指定します。  
  
## <a name="remarks"></a>解説  
 アプリケーション ロールが保護可能なアイテムを所有している場合は削除できません。 セキュリティ保護可能なリソースを所有しているアプリケーション ロールを削除するには、先にセキュリティ保護可能なリソースの所有権を譲渡するか削除する必要があります。  
  
> [!CAUTION]  
>  [!INCLUDE[ssCautionUserSchema](../../includes/sscautionuserschema-md.md)]  
  
## <a name="permissions"></a>Permissions  
 データベースに対する ALTER ANY APPLICATION ROLE 権限が必要です。  
  
## <a name="examples"></a>使用例  
 データベースからアプリケーション ロール "weekly_ledger" を削除します。  
  
```  
DROP APPLICATION ROLE weekly_ledger;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [アプリケーション ロール](../../relational-databases/security/authentication-access/application-roles.md)   
 [APPLICATION ROLE &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-application-role-transact-sql.md)   
 [ALTER APPLICATION ROLE &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-application-role-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
