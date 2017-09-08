---
title: "CLOSE MASTER KEY (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/15/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CLOSE MASTER KEY
- CLOSE_MASTER_KEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- encryption [SQL Server], Database Master Key
- CLOSE MASTER KEY statement
- database master key [SQL Server], closing
- cryptography [SQL Server], Database Master Key
- closing Database Master Keys
ms.assetid: bb04ef7a-9f3a-437e-a6f9-ba0204082cb9
caps.latest.revision: 30
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9e1337667bc7dd03d9943f7b7f76f8a313eeb125
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="close-master-key-transact-sql"></a>CLOSE MASTER KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  現在のデータベースのマスター キーを閉じます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
CLOSE MASTER KEY  
```  
  
## <a name="arguments"></a>引数  
 引数はありません。  
  
## <a name="remarks"></a>解説  
 このステートメントでは、OPEN MASTER KEY によって実行される操作の逆が実行されます。 CLOSE MASTER KEY は、データベース マスター キーが、現在のセッションで OPEN MASTER KEY ステートメントを使って開かれたときにのみ成功します。  
  
## <a name="permissions"></a>Permissions  
 権限は必要ありません。  
  
## <a name="examples"></a>使用例  
  
```  
USE AdventureWorks2012;  
CLOSE MASTER KEY;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
```  
USE master;  
OPEN MASTER KEY DECRYPTION BY PASSWORD = '43987hkhj4325tsku7';  
GO   
CLOSE MASTER KEY;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [CREATE MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-master-key-transact-sql.md)   
 [MASTER KEY &#40; を開くTRANSACT-SQL と #41 です。](../../t-sql/statements/open-master-key-transact-sql.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  


