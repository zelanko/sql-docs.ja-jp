---
title: "sys.key_encryptions (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.key_encryptions
- key_encryptions_TSQL
- sys.key_encryptions_TSQL
- key_encryptions
dev_langs: TSQL
helpviewer_keywords: sys.key_encryptions catalog view
ms.assetid: c39cecf8-af63-40b9-98e5-f84a5bf3ae54
caps.latest.revision: "22"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ba1c62078f0400436a21749b28c302d2f8a2509e
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="syskeyencryptions-transact-sql"></a>sys.key_encryptions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  CREATE SYMMETRIC KEY ステートメントの ENCRYPTION BY 句で指定された対称キーの暗号化ごとに 1 行のデータを返します。  

  
|列名|データ型|Description|  
|------------------|----------------|-----------------|  
|**key_id を指定**|**int**|暗号化されたキーの ID。|  
|**拇印**|**varbinary (32)**|キーの暗号化で使用された証明書の SHA-1 ハッシュ。または、キーの暗号化で使用された対称キーの GUID。|  
|**crypt_type**|**char(4)**|暗号化の種類。<br /><br /> ESKS = 対称キーによる暗号化<br /><br /> ESKP、ESP2、または ESP3 = パスワードによる暗号化<br /><br /> EPUC = 証明書による暗号化<br /><br /> EPUA = 非対称キーによる暗号化<br /><br /> ESKM = マスター キーによる暗号化|  
|**crypt_type_desc**|**nvarchar (60)**|暗号化の種類の説明:<br /><br /> ENCRYPTION BY SYMMETRIC KEY<br /><br /> ENCRYPTION BY PASSWORD <br />(以降で[!INCLUDE[sssqlv14_md](../../includes/sssqlv14-md.md)]CSS で使用するためのバージョン番号が含まれています)。<br /><br /> ENCRYPTION BY CERTIFICATE<br /><br /> ENCRYPTION BY ASYMMETRIC KEY<br /><br /> ENCRYPTION BY MASTER KEY<br /><br /> 注: Windows DPAPI は、サービス マスター _ キーの保護に使用されます。|  
|**crypt_property**|**varbinary(max)**|署名された、または暗号化されたビット。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [セキュリティ カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)  
  
  
