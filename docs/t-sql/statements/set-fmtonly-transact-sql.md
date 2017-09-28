---
title: "SET FMTONLY (TRANSACT-SQL) |Microsoft ドキュメント"
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
- FMTONLY_TSQL
- FMTONLY
- SET FMTONLY
- SET_FMTONLY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- metadata [SQL Server], only metadata returned
- SET FMTONLY statement
- FMTONLY option
ms.assetid: 02a1d9ac-2e58-433c-9a07-2c5a4a2214e1
caps.latest.revision: 48
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1cf925ce8ec9095acec90a34ed7d08f04826c2c1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="set-fmtonly-transact-sql"></a>SET FMTONLY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  メタデータだけをクライアントに返します。 クエリを実際に実行しなくても、応答の形式をテストすることができます。  
  
> [!NOTE]  
>  この機能は使用しないでください。 この機能は置き換えられました[sp_describe_first_result_set & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md)、 [sp_describe_undeclared_parameters & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-describe-undeclared-parameters-transact-sql.md)、 [sys.dm_exec_describe_first_result_set & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-transact-sql.md)、および[sys.dm_exec_describe_first_result_set_for_object & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-for-object-transact-sql.md).  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
SET FMTONLY { ON | OFF }   
```  
  
## <a name="remarks"></a>解説  
 SET FMTONLY を ON に設定している場合、行は処理されず、また要求の結果としてクライアントに送られません。  
  
 SET FMTONLY は、解析時ではなく実行時に設定されます。  
  
## <a name="permissions"></a>Permissions  
 public ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-view-the-column-header-information-for-a-query-without-actually-running-the-query"></a>A: は、実際にクエリを実行しなくても、クエリの列のヘッダー情報を表示します。  
 次の例の変更、`SET FMTONLY`設定`ON`を実行し、`SELECT`ステートメントです。 この設定では、ステートメントから列情報だけが返され、行は返されません。  
  
```  
USE AdventureWorks2012;  
GO  
SET FMTONLY ON;  
GO  
SELECT *   
FROM HumanResources.Employee;  
GO  
SET FMTONLY OFF;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="b-view-the-column-header-information-for-a-query-without-actually-running-the-query"></a>B. 実際にクエリを実行しなくても、クエリの列のヘッダー情報を表示します。  
 次の例では、クエリの列ヘッダー (メタデータ) の情報のみを返す方法を示します。 バッチは FMTONLY OFF に設定を開始し、FMTONLY を ON に、SELECT ステートメントの前に変更します。 これにより、列ヘッダーだけを返す SELECT ステートメントデータの行は返されません。  
  
```  
-- Uses AdventureWorks  
  
BEGIN  
    SET FMTONLY OFF;  
    SET DATEFORMAT mdy;  
    SET FMTONLY ON;  
    SELECT * FROM dbo.DimCustomer;  
    SET FMTONLY OFF;  
END  
  
```  
  
## <a name="see-also"></a>参照  
 [SET ステートメント &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)  
  
  


