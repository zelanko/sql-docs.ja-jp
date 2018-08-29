---
title: sys.key_encryptions (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 07/18/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.key_encryptions
- key_encryptions_TSQL
- sys.key_encryptions_TSQL
- key_encryptions
dev_langs:
- TSQL
helpviewer_keywords:
- sys.key_encryptions catalog view
ms.assetid: c39cecf8-af63-40b9-98e5-f84a5bf3ae54
caps.latest.revision: 22
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: bdf0a9a1232fdb986499bc1f50e2e3062df2c500
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43066534"
---
# <a name="syskeyencryptions-transact-sql"></a>sys.key_encryptions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  CREATE SYMMETRIC KEY ステートメントの ENCRYPTION BY 句で指定された対称キーの暗号化ごとに 1 行のデータを返します。  

  
|列名|データ型|説明|  
|------------------|----------------|-----------------|  
|**key_id**|**int**|暗号化されたキーの ID。|  
|**拇印**|**varbinary(32)**|キーの暗号化で使用された証明書の SHA-1 ハッシュ。または、キーの暗号化で使用された対称キーの GUID。|  
|**crypt_type**|**char(4)**|暗号化の種類。<br /><br /> ESKS = 対称キーによる暗号化<br /><br /> ESKP、ESP2、または ESP3 = パスワードによる暗号化<br /><br /> EPUC = 証明書による暗号化<br /><br /> EPUA = 非対称キーによる暗号化<br /><br /> ESKM = マスター キーによる暗号化|  
|**crypt_type_desc**|**nvarchar(60)**|暗号化の種類の説明です。<br /><br /> ENCRYPTION BY SYMMETRIC KEY<br /><br /> ENCRYPTION BY PASSWORD <br />(以降で[!INCLUDE[sssqlv14_md](../../includes/sssqlv14-md.md)]CSS で使用するためのバージョン番号が含まれています)。<br /><br /> ENCRYPTION BY CERTIFICATE<br /><br /> ENCRYPTION BY ASYMMETRIC KEY<br /><br /> ENCRYPTION BY MASTER KEY<br /><br /> 注: Windows DPAPI は、サービス マスター _ キーを保護するために使用されます。|  
|**crypt_property**|**varbinary(max)**|署名された、または暗号化されたビット。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [セキュリティ カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)  
  
  
