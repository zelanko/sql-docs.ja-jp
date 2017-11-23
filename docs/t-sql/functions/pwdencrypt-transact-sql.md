---
title: "PWDENCRYPT (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PWDENCRYPT
- PWDENCRYPT_TSQL
dev_langs: TSQL
helpviewer_keywords: PWDENCRYPT function [Transact-SQL]
ms.assetid: 333e9a43-1099-4b9b-b941-4b0b016f47f3
caps.latest.revision: "9"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 06b080d784d9a8737c1fe524e6634517ca0c97f5
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="pwdencrypt-transact-sql"></a>PWDENCRYPT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在のバージョンのパスワード ハッシュ アルゴリズムを使用して、入力値の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パスワード ハッシュを返します。  
  
 PWDENCRYPT は古い関数であり、将来の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] リリースではサポートされない可能性があります。 使用して[HASHBYTES](../../t-sql/functions/hashbytes-transact-sql.md)代わりにします。 HASHBYTES では、より多くのハッシュ アルゴリズムを使用できます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
PWDENCRYPT ( 'password' )  
```  
  
## <a name="arguments"></a>引数  
 *パスワード*  
 暗号化されるパスワードです。 *パスワード*は**sysname**です。  
  
## <a name="return-types"></a>戻り値の型  
 **varbinary (128)**  
  
## <a name="permissions"></a>Permissions  
 PWDENCRYPT は、パブリックで使用できます。  
  
## <a name="see-also"></a>参照  
 [セキュリティ関数 &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)   
 [PWDCOMPARE と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/pwdcompare-transact-sql.md)  
  
  
