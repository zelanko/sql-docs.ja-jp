---
title: "SET NUMERIC_ROUNDABORT (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- NUMERIC_ROUNDABORT
- SET_NUMERIC_ROUNDABORT_TSQL
- SET NUMERIC_ROUNDABORT
- NUMERIC_ROUNDABORT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- rounding expressions
- precision [SQL Server], rounded expressions
- expressions [SQL Server], rounding
- NUMERIC_ROUNDABORT
- SET NUMERIC_ROUNDABORT statement
ms.assetid: d20e74f1-b8da-466c-b180-9d8a8b851a77
caps.latest.revision: 33
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2885429909ebc48294d84d5f3b3a27bccca8abff
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="set-numericroundabort-transact-sql"></a>SET NUMERIC_ROUNDABORT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  式の丸め処理で精度が低下するときに作成されるエラー レポートのレベルを指定します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
SET NUMERIC_ROUNDABORT { ON | OFF }   
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
SET NUMERIC_ROUNDABORT ON;  
```  
  
## <a name="remarks"></a>解説  
 SET NUMERIC_ROUNDABORT が ON の場合には、式の精度が低下するとエラーが生成されます。 OFF の場合には、精度が低下してもエラー メッセージは生成されず、結果を格納する列または変数の精度に合わせて結果が丸められます。  
  
 固定精度の値を、それより精度の低い列または変数に格納しようとすると、精度が低下します。  
  
 SET NUMERIC_ROUNDABORT が ON の場合には、生成されるエラーの重大度は SET ARITHABORT によって決定されます。 次の表は、精度が低下するときにこの 2 つの設定がどのように影響するかを示しています。  
  
|設定|SET NUMERIC_ROUNDABORT ON|SET NUMERIC_ROUNDABORT OFF|  
|-------------|--------------------------------|---------------------------------|  
|SET ARITHABORT ON|エラーが生成されます。結果セットは返されません。|エラーや警告は返されません。結果は丸められます。|  
|SET ARITHABORT OFF|警告が返されます。式は NULL を返します。|エラーや警告は返されません。結果は丸められます。|  
  
 SET NUMERIC_ROUNDABORT は、解析時ではなく実行時に設定されます。  
  
 計算列やインデックス付きビューのインデックスを作成または変更するときには、SET NUMERIC_ROUNDABORT を OFF に設定する必要があります。 SET NUMERIC_ROUNDABORT が ON の場合、計算列にインデックスが設定されているテーブルやインデックス付きビューにおける CREATE、UPDATE、INSERT、および DELETE の各ステートメントは失敗します。 計算列でインデックス付きビューとインデックスを持つ必要な SET オプション設定に関する詳細についてを参照してください「の考慮事項とする SET ステートメントの使用」 [SET ステートメント & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-statements-transact-sql.md).  
  
 この設定の現在の設定を表示するには、次のクエリを実行します。  
  
```  
DECLARE @NUMERIC_ROUNDABORT VARCHAR(3) = 'OFF';  
IF ( (8192 & @@OPTIONS) = 8192 ) SET @NUMERIC_ROUNDABORT = 'ON';  
SELECT @NUMERIC_ROUNDABORT AS NUMERIC_ROUNDABORT;  
  
```  
  
## <a name="permissions"></a>Permissions  
 ロール **public** のメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、小数点以下 4 桁の精度の 2 つの値を加算して、小数点以下 2 桁の変数に格納します。 この式は、`SET NUMERIC_ROUNDABORT` と `SET ARITHABORT` の 2 つの設定の結果を示します。  
  
```  
-- SET NOCOUNT to ON,   
-- SET NUMERIC_ROUNDABORT to ON, and SET ARITHABORT to ON.  
SET NOCOUNT ON;  
PRINT 'SET NUMERIC_ROUNDABORT ON';  
PRINT 'SET ARITHABORT ON';  
SET NUMERIC_ROUNDABORT ON;  
SET ARITHABORT ON;  
GO  
DECLARE @result DECIMAL(5, 2),  
   @value_1 DECIMAL(5, 4),   
   @value_2 DECIMAL(5, 4);  
SET @value_1 = 1.1234;  
SET @value_2 = 1.1234 ;  
SELECT @result = @value_1 + @value_2;  
SELECT @result;  
GO  
  
-- SET NUMERIC_ROUNDABORT to ON and SET ARITHABORT to OFF.  
PRINT 'SET NUMERIC_ROUNDABORT ON';  
PRINT 'SET ARITHABORT OFF';  
SET NUMERIC_ROUNDABORT ON;  
SET ARITHABORT OFF;  
GO  
DECLARE @result DECIMAL(5, 2),  
   @value_1 DECIMAL(5, 4),   
   @value_2 DECIMAL(5, 4);  
SET @value_1 = 1.1234;  
SET @value_2 = 1.1234 ;  
SELECT @result = @value_1 + @value_2;  
SELECT @result;  
GO  
  
-- SET NUMERIC_ROUNDABORT to OFF and SET ARITHABORT to ON.  
PRINT 'SET NUMERIC_ROUNDABORT OFF';  
PRINT 'SET ARITHABORT ON';  
SET NUMERIC_ROUNDABORT OFF;  
SET ARITHABORT ON;  
GO  
DECLARE @result DECIMAL(5, 2),  
   @value_1 DECIMAL(5, 4),   
   @value_2 DECIMAL(5, 4);  
SET @value_1 = 1.1234;  
SET @value_2 = 1.1234 ;  
SELECT @result = @value_1 + @value_2;  
SELECT @result;  
GO  
  
-- SET NUMERIC_ROUNDABORT to OFF and SET ARITHABORT to OFF.  
PRINT 'SET NUMERIC_ROUNDABORT OFF';  
PRINT 'SET ARITHABORT OFF';  
SET NUMERIC_ROUNDABORT OFF;  
SET ARITHABORT OFF;  
GO  
DECLARE @result DECIMAL(5, 2),  
   @value_1 DECIMAL(5, 4),   
   @value_2 DECIMAL(5, 4);  
SET @value_1 = 1.1234;  
SET @value_2 = 1.1234;  
SELECT @result = @value_1 + @value_2;  
SELECT @result;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [SET ステートメント &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET ARITHABORT & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-arithabort-transact-sql.md)  
  
  
