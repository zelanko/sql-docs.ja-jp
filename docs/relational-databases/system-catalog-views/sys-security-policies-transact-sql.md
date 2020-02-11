---
title: security_policies (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- SYS.SECURITY_POLICIES_TSQL
- SECURITY_POLICIES_TSQL
- SYS.SECURITY_POLICIES
- SECURITY_POLICIES
dev_langs:
- TSQL
helpviewer_keywords:
- sys.security_policies catalog view
- security_policies catalog view
ms.assetid: 35362f5b-e601-4049-9e1d-c5307e823831
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||>=sql-server-2016||=azure-sqldw-latest||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d6eec5c523e2bdd321af145f19d0b5e7e7cba39b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68135309"
---
# <a name="syssecurity_policies-transact-sql"></a>security_policies (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  データベース内のセキュリティポリシーごとに1行のデータを返します。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|name|**sysname**|セキュリティポリシーの名前。データベース内で一意です。|  
|object_id|**int**|セキュリティポリシーの ID。|  
|principal_id|**int**|データベースに登録されているセキュリティポリシーの所有者の ID。 スキーマを使用して所有者が決定される場合は NULL です。|  
|schema_id|**int**|オブジェクトが存在するスキーマの ID。|  
|parent_object_id|**int**|ポリシーが所属するオブジェクトの ID。 0 を指定する必要があります。|  
|型|**vachar (2)**|**SP**である必要があります。|  
|type_desc|**nvarchar (60)**|**SECURITY_POLICY**。|  
|create_date|**DATETIME**|セキュリティポリシーが作成された UTC 日付。|  
|modify_date|**DATETIME**|セキュリティポリシーが最後に変更された UTC 日付。|  
|is_ms_shipped|**bit**|常に false です。|  
|is_enabled|**bit**|セキュリティポリシー仕様の状態:<br /><br /> 0 = 無効<br /><br /> 1 = 有効|  
|is_not_for_replication|**bit**|ポリシーは NOT FOR REPLICATION オプションを使用して作成されました。|  
|uses_database_collation|**bit**|では、データベースと同じ照合順序が使用されます。|  
|is_schemabinding_enabled|**bit**|セキュリティポリシーの Schemabinding の状態:<br /><br /> 0または NULL = 有効<br /><br /> 1 = 無効|  
  
## <a name="permissions"></a>アクセス許可  
 **ALTER ANY SECURITY POLICY**権限を持つプリンシパルは、このカタログビュー内のすべてのオブジェクトと、そのオブジェクトに対する**view DEFINITION**を持つすべてのユーザーにアクセスできます。  
  
## <a name="see-also"></a>参照  
 [行レベルのセキュリティ](../../relational-databases/security/row-level-security.md)   
 [security_predicates &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-security-predicates-transact-sql.md)   
 [Transact-sql&#41;&#40;セキュリティポリシーを作成する](../../t-sql/statements/create-security-policy-transact-sql.md)   
 [セキュリティカタログビュー &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [プリンシパル &#40;データベースエンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
