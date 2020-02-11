---
title: sys. openkeys (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- openkeys_TSQL
- sys.openkeys_TSQL
- openkeys
- sys.openkeys
dev_langs:
- TSQL
helpviewer_keywords:
- sys.openkeys catalog view
ms.assetid: 719a1259-2398-4fcb-ba05-aeabba7aec21
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f1ef2a7b5bdff79c3d12441f09ab2a05439f7a61
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68125375"
---
# <a name="sysopenkeys-transact-sql"></a>sys.openkeys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  このカタログビューは、現在のセッションで開いている暗号化キーに関する情報を返します。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|キーが格納されているデータベースの ID。|  
|**database_name**|**sysname**|キーを含んでいるデータベースの名前。|  
|**key_id**|**int**|キーの ID。 ID はデータベース内で一意です。|  
|**key_name**|**sysname**|キーの名前。 データベース内で一意です。|  
|**key_guid**|**varbinary**|キーの GUID。 データベース内で一意です。|  
|**opened_date**|**DATETIME**|キーが開かれた日付と時刻。|  
|**オンライン**|**int**|キーがメタデータで有効である場合は1。 キーがメタデータ内で見つからない場合は 0 です。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]詳細については、「[メタデータ表示の構成](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [OPEN SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/open-symmetric-key-transact-sql.md)  
  
  
