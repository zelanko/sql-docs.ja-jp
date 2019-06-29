---
title: KEY_GUID (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Key_GUID_TSQL
- Key_GUID
dev_langs:
- TSQL
helpviewer_keywords:
- symmetric keys [SQL Server], GUIDs
- KEY_GUID function
- GUIDs [SQL Server]
ms.assetid: 9246c7b2-7098-42c4-a222-cbf30267c46a
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: b39f2b1898678b06d77c89eed513927d6dfc92b3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "65949229"
---
# <a name="keyguid-transact-sql"></a>KEY_GUID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  データベース内の対称キーの GUID を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
Key_GUID( 'Key_Name' )  
```  
  
## <a name="arguments"></a>引数  
 **'** *Key_Name* **'**  
 データベース内の対称キーの名前を指定します。  
  
## <a name="return-types"></a>戻り値の型  
 **uniqueidentifier**  
  
## <a name="remarks"></a>Remarks  
 キーの作成時に ID 値が指定された場合、その GUID はその ID 値の MD5 ハッシュです。 ID 値が指定されなかった場合は、サーバーによって GUID が生成されています。  
  
 一時キーの場合、キー名の先頭は番号記号 (#) でなければなりません。  
  
## <a name="permissions"></a>アクセス許可  
 一時キーは、そのキーが作成されたセッションでのみ使用できます。したがって、アクセスに必要な権限はありません。 一時キーでないキーにアクセスするには、呼び出し側がそのキーに対して権限を持っている必要があり、またキーに対する VIEW 権限が拒否されていないことが条件となります。  
  
## <a name="examples"></a>使用例  
 次の例では、`ABerglundKey1` という対称キーの GUID を返します。  
  
```  
SELECT Key_GUID('ABerglundKey1');  
```  
  
## <a name="see-also"></a>参照  
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [sys.symmetric_keys &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-symmetric-keys-transact-sql.md)   
 [sys.key_encryptions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-key-encryptions-transact-sql.md)  
  
  
