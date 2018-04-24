---
title: SET CONCAT_NULL_YIELDS_NULL (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-data-warehouse, pdw, sql-database
ms.service: ''
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CONCAT_NULL_YIELDS_NULL_TSQL
- SET CONCAT_NULL_YIELDS_NULL
- CONCAT_NULL_YIELDS_NULL
- SET_CONCAT_NULL_YIELDS_NULL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CONCAT_NULL_YIELDS_NULL option
- null values [SQL Server], concatenation results
- concatenation [SQL Server]
- SET CONCAT_NULL_YIELDS_NULL statement
ms.assetid: 3091b71c-6518-4eb4-88ab-acae49102bc5
caps.latest.revision: 34
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: a07b9db8f3f444587eb23cd1dfd92c9814da9e2f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="set-concatnullyieldsnull-transact-sql"></a>SET CONCAT_NULL_YIELDS_NULL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  連結の結果が NULL として取り扱われるのか、空文字列として取り扱われるのかを制御します。  
  
> [!IMPORTANT]  
>  今後のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、CONCAT_NULL_YIELDS_NULL が常に ON になり、このオプションを明示的に OFF に設定するすべてのアプリケーションでエラーが発生します。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server  
    
SET CONCAT_NULL_YIELDS_NULL { ON | OFF }   
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
SET CONCAT_NULL_YIELDS_NULL ON    
```  
  
## <a name="remarks"></a>Remarks  
 SET CONCAT_NULL_YIELDS_NULL が ON の場合、NULL 値を文字列と連結すると、結果は NULL になります。 たとえば、`SELECT 'abc' + NULL` の結果は `NULL` になります。 SET CONCAT_NULL_YIELDS_NULL が OFF の場合、NULL 値を文字列と連結すると、結果は元の文字列になり、NULL 値は空文字列として扱われます。 たとえば、`SELECT 'abc' + NULL` の結果は `abc` になります。  
  
 SET CONCAT_NULL_YIELDS_NULL を指定しなかった場合は、**CONCAT_NULL_YIELDS_NULL** データベース オプションの設定が適用されます。  
  
> [!NOTE]  
>  SET CONCAT_NULL_YIELDS_NULL は、ALTER DATABASE の CONCAT_NULL_YIELDS_NULL 設定と同じ設定です。  
  
 SET CONCAT_NULL_YIELDS_NULL は、解析時ではなく実行時に設定されます。  
  
 計算列やインデックス付きビューのインデックスを作成または変更するときには、SET CONCAT_NULL_YIELDS_NULL を ON に設定する必要があります。 SET CONCAT_NULL_YIELDS_NULL が OFF の場合、計算列にインデックスが設定されているテーブルやインデックス付きビューにおける CREATE、UPDATE、INSERT、および DELETE のステートメントはいずれも失敗します。 インデックス付きビューおよび計算列上のインデックスに必要な SET オプション設定の詳細については、「[SET ステートメント &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)」の「SET ステートメントの使用に関する留意事項」を参照してください。  
  
 CONCAT_NULL_YIELDS_NULL を OFF に設定した場合、複数のサーバーにまたがって文字列を連結することはできません。  
  
 この設定の現在の設定を表示するには、次のクエリを実行します。  
  
```  
DECLARE @CONCAT_NULL_YIELDS_NULL VARCHAR(3) = 'OFF';  
IF ( (4096 & @@OPTIONS) = 4096 ) SET @CONCAT_NULL_YIELDS_NULL = 'ON';  
SELECT @CONCAT_NULL_YIELDS_NULL AS CONCAT_NULL_YIELDS_NULL;  
  
```  
  
## <a name="examples"></a>使用例  
 次の例では、両方の `SET CONCAT_NULL_YIELDS_NULL` 設定を示します。  
  
```  
PRINT 'Setting CONCAT_NULL_YIELDS_NULL ON';  
GO  
-- SET CONCAT_NULL_YIELDS_NULL ON and testing.  
SET CONCAT_NULL_YIELDS_NULL ON;  
GO  
SELECT 'abc' + NULL ;  
GO  
  
-- SET CONCAT_NULL_YIELDS_NULL OFF and testing.  
SET CONCAT_NULL_YIELDS_NULL OFF;  
GO  
SELECT 'abc' + NULL;   
GO  
```  
  
## <a name="see-also"></a>参照  
 [SET ステートメント &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SESSIONPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/sessionproperty-transact-sql.md)  
  
  
