---
title: security_predicates (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
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
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||>=sql-server-2016||=azure-sqldw-latest||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 6cf464370c5c2ca3f5075205c6783e9332309f12
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68135222"
---
# <a name="syssecurity_predicates-transact-sql"></a>security_predicates (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  データベース内のセキュリティ述語ごとに1行のデータを返します。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|object_id|**int**|この述語を含むセキュリティポリシーの ID。|  
|security_predicate_id|**int**|このセキュリティポリシー内の述語 ID。|  
|target_object_id|**int**|セキュリティ述語がバインドされるオブジェクトの ID。|  
|predicate_definition|**nvarchar(max)**|引数を含むセキュリティ述語として使用される関数の完全修飾名。 名前が正規化`schema.function`されている可能性があることに注意してください (つまり、エスケープされます)。また、一貫性を確保するためにテキスト内のその他の要素も同様です。 次に例を示します。<br /><br /> `[dbo].[fn_securitypredicate]([wing], [startTime], [endTime])`|  
|predicate_type|**int**|セキュリティポリシーによって使用される述語の種類。<br /><br /> 0 = フィルター述語<br /><br /> 1 = ブロック述語|  
|predicate_type_desc|**nvarchar (60)**|セキュリティポリシーによって使用される述語の種類。<br /><br /> FILTER<br /><br /> ブロック|  
|operation|**int**|述語に対して指定された操作の種類。<br /><br /> NULL = 適用可能なすべての操作<br /><br /> 1 = 挿入後<br /><br /> 2 = 更新後<br /><br /> 3 = 更新前<br /><br /> 4 = 削除前|  
|operation_desc|**nvarchar (60)**|述語に対して指定された操作の種類。<br /><br /> NULL<br /><br /> 挿入後<br /><br /> 更新後に<br /><br /> 更新前<br /><br /> 削除前|  
  
## <a name="permissions"></a>アクセス許可  
 **ALTER ANY SECURITY POLICY**権限を持つプリンシパルは、このカタログビュー内のすべてのオブジェクトと、そのオブジェクトに対する**view DEFINITION**を持つすべてのユーザーにアクセスできます。  
  
## <a name="see-also"></a>参照  
 [行レベルのセキュリティ](../../relational-databases/security/row-level-security.md)   
 [security_policies &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-security-policies-transact-sql.md)   
 [Transact-sql&#41;&#40;セキュリティポリシーを作成する](../../t-sql/statements/create-security-policy-transact-sql.md)   
 [セキュリティカタログビュー &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [プリンシパル &#40;データベースエンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
