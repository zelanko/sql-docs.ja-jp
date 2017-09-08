---
title: "SET IDENTITY_INSERT (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET IDENTITY_INSERT
- SET_IDENTITY_INSERT_TSQL
- IDENTITY_INSERT_TSQL
- IDENTITY_INSERT
dev_langs:
- TSQL
helpviewer_keywords:
- IDENTITY_INSERT option
- SET IDENTITY_INSERT statement
- identity values [SQL Server], explicit values
- identity columns [SQL Server], explicit values
ms.assetid: a5dd49f2-45c7-44a8-b182-e0a5e5c373ee
caps.latest.revision: 26
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9725d774075f21fc86d5276c91ed281fa34eba7d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="set-identityinsert-transact-sql"></a>SET IDENTITY_INSERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  テーブルの ID 列に明示的な値を追加することを許可します。  

 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
SET IDENTITY_INSERT [ database_name . [ schema_name ] . ] table { ON | OFF }  
```  
  
## <a name="arguments"></a>引数  
 *database_name*  
 指定したテーブルが含まれているデータベースの名前を指定します。  
  
 *schema_name*  
 テーブルが所属するスキーマの名前を指定します。  
  
 *テーブル*  
 ID 列があるテーブルの名前を指定します。  
  
## <a name="remarks"></a>解説  
 IDENTITY_INSERT プロパティを ON に設定できるのは、セッション内の 1 つのテーブルのみです。 テーブルは既にこのプロパティを ON に設定し、別のテーブルに対して SET IDENTITY_INSERT ON ステートメントが実行された場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]SET IDENTITY_INSERT を示すエラー メッセージは既にとを ON に設定されているテーブルのレポートを返します。  
  
 挿入する値がテーブルの現在の ID 値よりも大きい場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では新しく挿入された値が現在の ID 値として自動的に使用されます。  
  
 SET IDENTITY_INSERT は、解析時ではなく実行時に設定されます。  
  
## <a name="permissions"></a>Permissions  
 ユーザーはテーブルを所有しているか、テーブルに対する ALTER 権限を持っている必要があります。  
  
## <a name="examples"></a>使用例  
 次の例では、ID 列を含むテーブルを作成した後、`SET IDENTITY_INSERT` ステートメントによって ID 値に発生したギャップを、`DELETE` の設定を使用して調整しています。  
  
```  
USE AdventureWorks2012;  
GO  
-- Create tool table.  
CREATE TABLE dbo.Tool(  
   ID INT IDENTITY NOT NULL PRIMARY KEY,   
   Name VARCHAR(40) NOT NULL  
);  
GO  
-- Inserting values into products table.  
INSERT INTO dbo.Tool(Name)   
VALUES ('Screwdriver')  
        , ('Hammer')  
        , ('Saw')  
        , ('Shovel');  
GO  
  
-- Create a gap in the identity values.  
DELETE dbo.Tool  
WHERE Name = 'Saw';  
GO  
  
SELECT *   
FROM dbo.Tool;  
GO  
  
-- Try to insert an explicit ID value of 3;  
-- should return a warning.  
INSERT INTO dbo.Tool (ID, Name) VALUES (3, 'Garden shovel');  
GO  
-- SET IDENTITY_INSERT to ON.  
SET IDENTITY_INSERT dbo.Tool ON;  
GO  
  
-- Try to insert an explicit ID value of 3.  
INSERT INTO dbo.Tool (ID, Name) VALUES (3, 'Garden shovel');  
GO  
  
SELECT *   
FROM dbo.Tool;  
GO  
-- Drop products table.  
DROP TABLE dbo.Tool;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [IDENTITY &#40;Property&#41; &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql-identity-property.md)   
 [SCOPE_IDENTITY と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/scope-identity-transact-sql.md)   
 [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
 [SET ステートメント &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)  
  
  

