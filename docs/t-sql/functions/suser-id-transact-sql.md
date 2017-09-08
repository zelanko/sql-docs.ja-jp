---
title: "SUSER_ID (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SUSER_ID_TSQL
- SUSER_ID
dev_langs:
- TSQL
helpviewer_keywords:
- users [SQL Server], IDs
- logins [SQL Server], IDs
- SUSER_ID function
- IDs [SQL Server], logins
- identification numbers [SQL Server], logins
- user IDs [SQL Server]
ms.assetid: 348911ab-b0b6-4867-aee7-e6f42e053a4a
caps.latest.revision: 22
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7e098c614f4e70cabf718ee4413920e61eb634c1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="suserid-transact-sql"></a>SUSER_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ユーザーのログイン ID 番号を返します。  
  
> [!NOTE]  
>  以降で[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、SUSER_ID として表示される値を返します**principal_id**で、 **sys.server_principals**カタログ ビューです。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
SUSER_ID ( [ 'login' ] )   
```  
  
## <a name="arguments"></a>引数  
 **'** *ログイン* **'**  
 ユーザーのログイン名を指定します。 *ログイン*は**nchar**です。 場合*ログイン*として指定された**char**、*ログイン*暗黙的に変換されます**nchar**です。 *ログイン*いずれかを指定できます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインまたは Windows ユーザーまたはグループのインスタンスに接続する権限を持つ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 場合*ログイン*が指定されていない、現在のユーザーのログイン id 番号が返されます。 パラメーターに "NULL" という語が含まれていると、NULL が返されます。  
  
## <a name="return-types"></a>戻り値の型  
 **int**  
  
## <a name="remarks"></a>解説  
 SUSER_ID は内に明示的にプロビジョニングされたログインに対してのみ、識別番号を返します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 この ID は内で使用される[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]所有権と権限を追跡するためにします。 この ID は、SUSER_SID によって返されるログインの SID と等価ではありません。 場合*ログイン*は、SQL Server ログインは GUID に SID マップします。 場合*ログイン*Windows ログインまたは Windows グループの SID が Windows セキュリティ識別子にマップします。  
  
 SUSER_SID を内のエントリを持つログインに対してのみ SUID を返します、 **syslogins**システム テーブル。  
  
 システム関数は、選択リストの中、WHERE 句の中、および式を使用できるすべての場所で使用できます。ただし、パラメーターを指定しない場合であっても、その後に常にかっこを指定する必要があります。  
  
## <a name="examples"></a>使用例  
 次の例は、ログインの識別番号を返します、`sa`ログインします。  
  
```  
SELECT SUSER_ID('sa');  
```  
  
## <a name="see-also"></a>参照  
 [sys.server_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [SUSER_SID & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/suser-sid-transact-sql.md)   
 [システム関数 & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/system-functions-for-transact-sql.md)  
  
  
