---
title: sys.security_predicates (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- Azure SQL Database
- SQL Server 2016 Preview
f1_keywords:
- SYS.SECURITY_PREDICATES
- SECURITY_PREDICATES
- SECURITY_PREDICATES_TSQL
- SYS.SECURITY_PREDICATES_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.security_predicates catalog view
- security_predicates catalog view
ms.assetid: c7a2f28c-98da-463d-8b8a-8e5619e2c6a6
caps.latest.revision: 9
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 539ca48e5c55485a5a4b3fdecb3044c1feae6826
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37993854"
---
# <a name="syssecuritypredicates-transact-sql"></a>sys.security_predicates (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  データベース内の各セキュリティ述語の行を返します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|object_id|**int**|この述語が含まれるセキュリティ ポリシーの ID。|  
|security_predicate_id|**int**|このセキュリティ ポリシー内の述語 ID。|  
|target_object_id|**int**|セキュリティ述語がバインドされるオブジェクトの ID。|  
|predicate_definition|**nvarchar(max)**|引数を含む、セキュリティ述語として使用される関数の完全修飾名。 なお、`schema.function`名前可能性があります (つまりエスケープされた) の正規化にする場合と一貫性を保つのためのテキストで他の要素。 以下に例を示します。<br /><br /> `[dbo].[fn_securitypredicate]([wing], [startTime], [endTime])`|  
|predicate_type|**int**|セキュリティ ポリシーによって使用される述語の種類。<br /><br /> 0 = フィルター述語<br /><br /> 1 = ブロックの述語|  
|predicate_type_desc|**nvarchar(60)**|セキュリティ ポリシーによって使用される述語の種類。<br /><br /> FILTER<br /><br /> ブロック|  
|operation|**int**|述語で指定された操作の種類。<br /><br /> NULL = 適用可能なすべての操作<br /><br /> 1 = 挿入後<br /><br /> 2 = 更新の後<br /><br /> 3 = 更新する前に<br /><br /> 4 = を削除する前に|  
|operation_desc|**nvarchar(60)**|述語で指定された操作の種類。<br /><br /> NULL<br /><br /> 挿入後<br /><br /> 更新後に<br /><br /> 更新する前に<br /><br /> 削除する前に|  
  
## <a name="permissions"></a>アクセス許可  
 持つプリンシパル、 **ALTER ANY SECURITY POLICY**アクセス許可がある、すべてのユーザーをこのカタログ ビューのすべてのオブジェクトへのアクセス**VIEW DEFINITION**オブジェクト。  
  
## <a name="see-also"></a>参照  
 [行レベルのセキュリティ](../../relational-databases/security/row-level-security.md)   
 [sys.security_policies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-security-policies-transact-sql.md)   
 [CREATE SECURITY POLICY &#40;Transact-SQL&#41;](../../t-sql/statements/create-security-policy-transact-sql.md)   
 [セキュリティ カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
