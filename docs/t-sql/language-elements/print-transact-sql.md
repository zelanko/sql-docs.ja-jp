---
title: "印刷 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PRINT_TSQL
- PRINT
dev_langs:
- TSQL
helpviewer_keywords:
- PRINT statement
- user-defined messages [SQL Server]
- messages [SQL Server], PRINT statement
- displaying user-defined messages
- viewing user-defined messages
- conditionally returning messages [SQL Server]
ms.assetid: 32ba0729-c4b5-4cfb-a5aa-e8b9402be028
caps.latest.revision: 33
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 51377ebe291fe4c76d8761aaba74eab8f5201108
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="print-transact-sql"></a>印刷 Transact SQL
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  ユーザー定義メッセージをクライアントに返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  

PRINT msg_str | @local_variable | string_expr  
```  
  
## <a name="arguments"></a>引数  
 *msg_str*  
 文字列または Unicode 文字列の定数です。 詳細については、次を参照してください。[定数 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/data-types/constants-transact-sql.md).  
  
 **@***local_variable*  
 任意の有効な文字型の変数を指定します。 **@***local_variable*する必要があります**char**、 **nchar**、 **varchar**、または**nvarchar**、またはあることができる必要がありますこれらのデータ型に暗黙的に変換します。  
  
 *string_expr*  
 文字列を返す式を指定します。 連結したリテラル値、関数、および変数を含むことができます。 詳細については、「[式 &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)」を参照してください。  
  
## <a name="remarks"></a>解説  
 メッセージ文字列は、Unicode 以外の文字列の場合は 8,000 バイトまで指定でき、Unicode 文字列の場合は 4,000 バイトまで指定できます。 これより長い文字列は切り詰められます。 **Varchar (max)**と**nvarchar (max)**大きさは、データ型へのデータ型は切り捨てられます**varchar (8000)**と**nvarchar(4000)**.  
  
 RAISERROR を使用してメッセージを返すこともできます。 RAISERROR には、PRINT にはない次のような利点があります。  
  
-   RAISERROR は、エラー メッセージ文字列への引数の置き換えをサポートします。この置き換えでは、C 言語標準ライブラリの printf 関数をモデルにしたメカニズムを使用します。  
  
-   RAISERROR では、テキスト メッセージに加えて、一意のエラー番号、重大度、および状態コードを指定できます。  
  
-   RAISERROR は、sp_addmessage システム ストアド プロシージャを使用して作成したユーザー定義メッセージを返すために使用できます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-conditionally-executing-print-if-exists"></a>A. 条件付きで PRINT を実行する (IF EXISTS)  
 次の例では、`PRINT`ステートメント条件付きでメッセージを返します。  
  
```  
IF @@OPTIONS & 512 <> 0  
    PRINT N'This user has SET NOCOUNT turned ON.';  
ELSE  
    PRINT N'This user has SET NOCOUNT turned OFF.';  
GO  
```  
  
### <a name="b-building-and-displaying-a-string"></a>B. 文字列を構築して表示する  
 次の例の結果の変換、`GETDATE`関数を`nvarchar`データ型で、によって返されるリテラル テキストと連結`PRINT`です。  
  
```  
-- Build the message text by concatenating  
-- strings and expressions.  
PRINT N'This message was printed on '  
    + RTRIM(CAST(GETDATE() AS nvarchar(30)))  
    + N'.';  
GO  
-- This example shows building the message text  
-- in a variable and then passing it to PRINT.  
-- This was required in SQL Server 7.0 or earlier.  
DECLARE @PrintMessage nvarchar(50);  
SET @PrintMessage = N'This message was printed on '  
    + RTRIM(CAST(GETDATE() AS nvarchar(30)))  
    + N'.';  
PRINT @PrintMessage;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-conditionally-executing-print"></a>C. 条件付きで print を実行します。  
 次の例では、`PRINT`ステートメント条件付きでメッセージを返します。  
  
```  
IF DB_ID() = 1  
    PRINT N'The current database is master.';  
ELSE  
    PRINT N'The current database is not master.';  
GO  
```  
  
### <a name="d-building-and-displaying-a-string"></a>D. 文字列を構築して表示する  
 次の例の結果の変換、`GETDATE`関数を`nvarchar`データ型で、によって返されるリテラル テキストと連結`PRINT`です。  
  
```  
-- Build the message text by concatenating  
-- strings and expressions.  
PRINT N'This message was printed on '  
    + RTRIM(CAST(GETDATE() AS nvarchar(30)))  
    + N'.';  
GO  
-- This example shows building the message text  
-- in a variable and then passing it to PRINT.  
DECLARE @PrintMessage nvarchar(50);  
SET @PrintMessage = N'This message was printed on '  
    + RTRIM(CAST(GETDATE() AS nvarchar(30)))  
    + N'.';  
PRINT @PrintMessage;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)   
 [RAISERROR と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/raiserror-transact-sql.md)  
  
  


