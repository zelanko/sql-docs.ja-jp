---
title: "DROP SIGNATURE (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP SIGNATURE
- DROP_SIGNATURE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- deleting signatures
- dropping signatures
- DROP SIGNATURE statement
- removing signatures
- signatures [SQL Server]
- digital signatures [SQL Server]
ms.assetid: 8a1fd8c5-0e75-4b2f-9d3c-c296bed56cc7
caps.latest.revision: 32
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 81823a549f608bdcddb631084904fb303a1ddc9f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="drop-signature-transact-sql"></a>DROP SIGNATURE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  ストアド プロシージャ、関数、トリガー、またはアセンブリからデジタル署名を削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
DROP [ COUNTER ] SIGNATURE FROM module_name   
    BY <crypto_list> [ ,...n ]  
  
<crypto_list> ::=  
    CERTIFICATE cert_name  
    | ASYMMETRIC KEY Asym_key_name  
```  
  
## <a name="arguments"></a>引数  
 *モジュール名*  
 ストアド プロシージャ、関数、トリガー、アセンブリ、またはイベント通知の名前を指定します。  
  
 証明書*cert_name*  
 ストアド プロシージャ、関数、トリガー、アセンブリ、またはイベント通知の署名に使用されている証明書の名前を指定します。  
  
 非対称キー *Asym_key_name*  
 ストアド プロシージャ、関数、アセンブリ、またはトリガーの署名に使用されている非対称キーの名前を指定します。  
  
## <a name="remarks"></a>解説  
 署名に関する情報は、sys.crypt_properties カタログ ビューで確認できます。  
  
## <a name="permissions"></a>Permissions  
 オブジェクトに対する ALTER 権限と、証明書または非対称キーに対する CONTROL 権限が必要です。 関連付けられている秘密キーがパスワードで保護されている場合、ユーザーはそのパスワードも保持している必要があります。  
  
## <a name="examples"></a>使用例  
 次の例では、証明書 `HumanResourcesDP` の署名を、ストアド プロシージャ `HumanResources.uspUpdateEmployeeLogin` から削除します。  
  
```  
USE AdventureWorks2012;  
DROP SIGNATURE FROM HumanResources.uspUpdateEmployeeLogin   
    BY CERTIFICATE HumanResourcesDP;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sys.crypt_properties & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-crypt-properties-transact-sql.md)   
 [署名を追加する & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/add-signature-transact-sql.md)  
  
  

