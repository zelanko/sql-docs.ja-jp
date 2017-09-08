---
title: "ドロップ資格情報 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/19/2015
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP CREDENTIAL
- DROP_CREDENTIAL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- removing credentials
- DROP CREDENTIAL statement
- credentials [SQL Server], DROP CREDENTIAL statement
- authentication [SQL Server], credentials
- deleting credentials
- dropping credentials
ms.assetid: df22c826-317d-45a6-b078-186acb65f71e
caps.latest.revision: 31
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 99526bd72839ff483d39f0e78634ea27039388ae
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="drop-credential-transact-sql"></a>DROP CREDENTIAL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サーバーから資格情報を削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
DROP CREDENTIAL credential_name  
```  
  
## <a name="arguments"></a>引数  
 *credential_name*  
 サーバーから削除する資格情報の名前を指定します。  
  
## <a name="remarks"></a>解説  
 資格情報自体を削除しない限り、資格情報に関連付けられているシークレットを削除するには、使用[ALTER CREDENTIAL](../../t-sql/statements/alter-credential-transact-sql.md)です。  
  
 資格情報に関する情報は、 **sys.credentials**カタログ ビューです。  
  
> [!WARNING]  
>  プロキシは、資格情報と関連付けられています。 プロキシが使用する資格情報を削除すると、関連付けられているプロキシが使用できない状態のままになります。 プロキシで使用する資格情報を削除する場合、プロキシの削除 (を使用して[sp_delete_proxy (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-delete-proxy-transact-sql.md)を使用して、関連付けられたプロキシを作成し直すと[sp_add_proxy (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-add-proxy-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 ALTER ANY CREDENTIAL 権限が必要です。 システム資格情報を削除するには、CONTROL SERVER 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例と呼ばれる資格情報を削除する`Saddles`です。  
  
```  
DROP CREDENTIAL Saddles;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [資格情報 (&) #40";"データベース エンジン"&"#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [ALTER CREDENTIAL &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-credential-transact-sql.md)   
 [データベース スコープの資格情報 &#40; を削除します。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-database-scoped-credential-transact-sql.md)   
 [sys.credentials &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
  
  

