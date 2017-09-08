---
title: "@@REMSERVER (TRANSACT-SQL) |Microsoft ドキュメント"
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
- '@@REMSERVER'
- '@@REMSERVER_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- logins [SQL Server], remote servers
- remote servers [SQL Server], logins
- '@@REMSERVER function'
ms.assetid: 0bb451a9-3866-4064-963d-b74a2f864049
caps.latest.revision: 23
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 23ae1a37bcc84561a0ccedf10b1bb0c6ee7b6b73
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="remserver-transact-sql"></a>@@REMSERVER (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)]代わりに、リンク サーバーとリンク サーバー ストアド プロシージャを使用します。  
  
 ログイン レコードに表示される、リモート [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース サーバーの名前を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
@@REMSERVER  
```  
  
## <a name="return-types"></a>戻り値の型  
 **nvarchar (128)**  
  
## <a name="remarks"></a>解説  
 @@REMSERVERプロシージャの実行元となるデータベース サーバーの名前を確認するストアド プロシージャを有効にします。  
  
## <a name="examples"></a>使用例  
 次の例では、プロシージャ`usp_CheckServer`を返すリモート サーバーの名前。  
  
```  
CREATE PROCEDURE usp_CheckServer  
AS  
SELECT @@REMSERVER;  
```  
  
 次のストアド プロシージャは、ローカル サーバーで作成された`SEATTLE1`です。 ユーザーはリモート サーバーの `LONDON2` にログインし、`usp_CheckServer` を実行します。  
  
```  
EXEC SEATTLE1...usp_CheckServer;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
---------------  
LONDON2  
```  
  
## <a name="see-also"></a>参照  
 [構成関数 &#40;Transact-SQL&#41;](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [リモート サーバー](../../database-engine/configure-windows/remote-servers.md)  
  
  
