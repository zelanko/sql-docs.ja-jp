---
title: IS_OBJECTSIGNED (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- IS_OBJECTSIGNED
- IS_OBJECTSIGNED_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IS_OBJECTSIGNED function
ms.assetid: afbc4f7f-8266-4ee6-9802-14a2dbe69ef6
caps.latest.revision: 16
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 104cf6916beca429e65610106cbdba5a289deeec
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="isobjectsigned-transact-sql"></a>IS_OBJECTSIGNED (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  オブジェクトが、指定した証明書または非対称キーで署名されているかどうかを示します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
IS_OBJECTSIGNED (   
'OBJECT', @object_id, @class, @thumbprint  
  )   
```  
  
## <a name="arguments"></a>引数  
 **'OBJECT'**  
 セキュリティ保護可能なクラスの型。  
  
 *@object_id*  
 テストされるオブジェクトの object_id。 *@object_id* のデータ型は **int** 型です。  
  
 *@class*  
 オブジェクトのクラス :  
  
-   'certificate'  
  
-   'asymmetric key'  
  
 *@class* のデータ型は **sysname** です。  
  
 *@thumbprint*  
 オブジェクトの SHA 拇印。 *@thumbprint* は **varbinary(32)** 型です。  
  
## <a name="returned-types"></a>返される型  
 **int**  
  
## <a name="remarks"></a>Remarks  
 IS_OBJECTSIGNED は、次の値を返します。  
  
|戻り値|Description|  
|------------------|-----------------|  
|NULL|オブジェクトが署名されていないか、オブジェクトが有効ではありません。|  
|0|オブジェクトは署名されていますが、署名が有効ではありません。|  
|@shouldalert|オブジェクトは署名されています。|  
  
## <a name="permissions"></a>アクセス許可  
 証明書または非対称キーに対する VIEW DEFINITION 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-displaying-extended-properties-on-a-database"></a>A. データベースの拡張プロパティを表示する  
 次の例では、**master** データベースの spt_fallback_db テーブルがスキーマ署名証明書によって署名されているかどうかをテストします。  
  
```  
USE master;  
-- Declare a variable to hold a thumbprint and an object name  
DECLARE @thumbprint varbinary(20), @objectname sysname;  
  
-- Populate the thumbprint variable with the thumbprint of   
-- the master database schema signing certificate  
SELECT @thumbprint = thumbprint   
FROM sys.certificates   
WHERE name LIKE '%SchemaSigningCertificate%';  
  
-- Populate the object name variable with a table name in master  
SELECT @objectname = 'spt_fallback_db';  
  
-- Query to see if the table is signed by the thumbprint  
SELECT @objectname AS [object name],  
IS_OBJECTSIGNED(  
'OBJECT', OBJECT_ID(@objectname), 'certificate', @thumbprint  
) AS [Is the object signed?] ;  
```  
  
## <a name="see-also"></a>参照  
 [sys.fn_check_object_signatures (&) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/sys-fn-check-object-signatures-transact-sql.md)  
  
  
