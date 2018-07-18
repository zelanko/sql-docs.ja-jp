---
title: DROP CREDENTIAL (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/19/2015
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 20aedcc74ed091e1a46dbb19ece465cce0d1bba6
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/04/2018
ms.locfileid: "37784473"
---
# <a name="drop-credential-transact-sql"></a>DROP CREDENTIAL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サーバーから資格情報を削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
DROP CREDENTIAL credential_name  
```  
  
## <a name="arguments"></a>引数  
 *credential_name*  
 サーバーから削除する資格情報の名前を指定します。  
  
## <a name="remarks"></a>Remarks  
 資格情報自体は削除せずに、資格情報に関連付けられているシークレットを削除するには、[ALTER CREDENTIAL](../../t-sql/statements/alter-credential-transact-sql.md) を使います。  
  
 資格情報に関する情報は、**sys.credentials** カタログ ビューで確認できます。  
  
> [!WARNING]  
>  プロキシは、資格情報と関連付けられています。 プロキシが使用する資格情報を削除すると、関連付けられているプロキシが使用できない状態のままになります。 プロキシが使用する資格情報を削除する場合は、[sp_delete_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-proxy-transact-sql.md) を使ってプロキシを削除した後、[sp_add_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-proxy-transact-sql.md) を使って関連付けられているプロキシを作成し直します。  
  
## <a name="permissions"></a>アクセス許可  
 ALTER ANY CREDENTIAL 権限が必要です。 システム資格情報を削除するには、CONTROL SERVER 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、資格情報 `Saddles` を削除します。  
  
```  
DROP CREDENTIAL Saddles;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [資格情報 &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [ALTER CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-credential-transact-sql.md)   
 [DROP DATABASE SCOPED CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-scoped-credential-transact-sql.md)   
 [sys.credentials &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
  
  
