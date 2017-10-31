---
title: "非対称キーを削除 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP ASYMMETRIC KEY
- DROP_ASYMMETRIC_KEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- asymmetric keys [SQL Server], removing
- removing asymmetric keys
- encryption [SQL Server], asymmetric keys
- DROP ASYMMETRIC KEY statement
- dropping asymmetric keys
- deleting asymmetric keys
- cryptography [SQL Server], asymmetric keys
ms.assetid: bf94ac07-9b62-4318-b55b-1eed8f3a1ac6
caps.latest.revision: 32
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f3737521ee178f9b7287f8d86e269973841d74c6
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="drop-asymmetric-key-transact-sql"></a>DROP ASYMMETRIC KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  データベースから非対称キーを削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
DROP ASYMMETRIC KEY key_name [ REMOVE PROVIDER KEY ]  
```  
  
## <a name="arguments"></a>引数  
 *key_name*  
 データベースから削除する非対称キーの名前を指定します。  
  
 REMOVE PROVIDER KEY  
 EKM デバイスから Extenisble キー管理 (EKM) キーを削除します。 拡張キー管理の詳細については、次を参照してください。[拡張キー管理 & #40 です。EKM &#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md).  
  
## <a name="remarks"></a>解説  
 データベース内の対称キーが非対称キーで暗号化されている場合、またはユーザーやログインが非対称キーにマップされる場合、非対称キーは削除できません。 このようなキーを削除するには、事前にそのキーにマップされるユーザーまたはログインを削除する必要があります。 また、その非対称キーで暗号化されているすべての対称キーを削除または変更する必要があります。 DROP ENCRYPTION オプションを使用することができます[ALTER SYMMETRIC KEY](../../t-sql/statements/alter-symmetric-key-transact-sql.md)非対称キーによって暗号化を解除します。  
  
 非対称キーのメタデータを使用してアクセスできる、 [sys.asymmetric_keys](../../relational-databases/system-catalog-views/sys-asymmetric-keys-transact-sql.md)カタログ ビューです。 非対称キー自体を、データベース内部から直接表示することはできません。  
  
 非対称キーが EKM デバイスの拡張キー管理 (EKM) にマップされており、REMOVE PROVIDER KEY オプションが指定されていない場合は、キーはデータベースから削除されますが、デバイスからは削除されません。 この場合、警告が発行されます。  
  
## <a name="permissions"></a>Permissions  
 非対称キーに対する CONTROL 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、非対称キーを削除する`MirandaXAsymKey6`から、`AdventureWorks2012`データベース。  
  
```  
USE AdventureWorks2012;  
DROP ASYMMETRIC KEY MirandaXAsymKey6;  
```  
  
## <a name="see-also"></a>参照  
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [ALTER ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-asymmetric-key-transact-sql.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [ALTER SYMMETRIC KEY & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-symmetric-key-transact-sql.md)  
  
  

