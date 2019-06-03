---
title: PWDENCRYPT (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- PWDENCRYPT
- PWDENCRYPT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- PWDENCRYPT function [Transact-SQL]
ms.assetid: 333e9a43-1099-4b9b-b941-4b0b016f47f3
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 024d7c4a043dbc4801d5eb39fe7b05d27ef7c2b5
ms.sourcegitcommit: 83f061304fedbc2801d8d6a44094ccda97fdb576
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2019
ms.locfileid: "65943225"
---
# <a name="pwdencrypt-transact-sql"></a>PWDENCRYPT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在のバージョンのパスワード ハッシュ アルゴリズムを使用して、入力値の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パスワード ハッシュを返します。  
  
 PWDENCRYPT は古い関数であり、将来の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] リリースではサポートされない可能性があります。 代わりに、[HASHBYTES](../../t-sql/functions/hashbytes-transact-sql.md) を使用します。 HASHBYTES にはさらに多くのハッシュ アルゴリズムが用意されています。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
PWDENCRYPT ( 'password' )  
```  
  
## <a name="arguments"></a>引数  
 *password*  
 暗号化されるパスワードです。 *パスワード* は **sysname**です。  
  
## <a name="return-types"></a>戻り値の型  
 **varbinary (128)**  
  
## <a name="permissions"></a>アクセス許可  
 PWDENCRYPT はパブリックに使用できます。  
  
## <a name="see-also"></a>参照  
 [セキュリティ関数 &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)   
 [PWDCOMPARE &#40;Transact-SQL&#41;](../../t-sql/functions/pwdcompare-transact-sql.md)  
  
  
