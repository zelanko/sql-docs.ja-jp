---
title: "Key_id を指定 (TRANSACT-SQL) |Microsoft ドキュメント"
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
- Key_ID
- Key_ID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- identification numbers [SQL Server], symmetric keys
- KEY_ID function
- symmetric keys [SQL Server], IDs
- IDs [SQL Server], symmetric keys
ms.assetid: d7309542-dbbe-41dc-b42e-5d9a1c8b4838
caps.latest.revision: 27
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: bb4684105e8f8e4a13c1df77437271c1e820dce2
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="keyid-transact-sql"></a>KEY_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  現在のデータベースの対称キーの ID を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
Key_ID ( 'Key_Name' )  
```  
  
## <a name="arguments"></a>引数  
 **'** *Key_Name* **'**  
 データベース内の対称キーの名前を指定します。  
  
## <a name="return-types"></a>戻り値の型  
 **int**  
  
## <a name="remarks"></a>解説  
 一時キーの名前は、番号記号 (#) で始める必要があります。  
  
## <a name="permissions"></a>Permissions  
 一時キーは、そのキーが作成されたセッションでのみ使用できます。したがって、アクセスに必要な権限はありません。 一時キーでないキーにアクセスするには、呼び出し側がそのキーに対して権限を持っている必要があり、またキーに対する VIEW 権限が拒否されていないことが必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-returning-the-id-of-a-symmetric-key"></a>A. 対称キーの ID を返す  
 次の例と呼ばれるキーの ID を返します`ABerglundKey1`です。  
  
```  
SELECT KEY_ID('ABerglundKey1');  
```  
  
### <a name="b-returning-the-id-of-a-temporary-symmetric-key"></a>B. 一時対称キーの ID を返す  
 次の例では、一時対称キーの ID を返します。 キー名の前に `#` が付いていることに注意してください。  
  
```  
SELECT KEY_ID('#ABerglundKey2');  
```  
  
## <a name="see-also"></a>参照  
 [KEY_GUID & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/key-guid-transact-sql.md)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [sys.symmetric_keys & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-symmetric-keys-transact-sql.md)   
 [sys.key_encryptions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-key-encryptions-transact-sql.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  

