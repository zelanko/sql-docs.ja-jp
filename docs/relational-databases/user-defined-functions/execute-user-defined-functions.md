---
title: "ユーザー定義関数の実行 | Microsoft Docs"
ms.custom: ""
ms.date: "10/24/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-udf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ユーザー定義関数の呼び出し"
  - "user-defined functions [SQL Server], executing"
ms.assetid: 0de7744d-9b73-463f-ae80-e31a020004b5
caps.latest.revision: 35
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 35
---
# ユーザー定義関数の実行
  Transact-SQL を使用してユーザー定義関数を実行する
  

> **注:** ユーザー定義関数の詳細については、「[ユーザー定義関数](https://msdn.microsoft.com/library/ms191007.aspx)」および「[CREATE FUNCTION (Transact SQL)](https://msdn.microsoft.com/library/ms186755.aspx)」を参照してください。 
  
 
##  <a name="BeforeYouBegin"></a> アンインストールの準備  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
 Transact-SQL では、*値*を使用するか、@*parameter_name*=*値*を使用し、パラメーターを指定できます。 パラメーターは、トランザクションの一部ではないです。そのため、トランザクションが後でロールバックの値にパラメーターが変更された場合、パラメーター戻すことはできません前の値にします。 呼び出し元に返される値は常に、モジュールから戻る時点での値になります。  
  
###  <a name="Security"></a> セキュリティ  
  
 [EXECUTE](https://msdn.microsoft.com/library/ms188332.aspx) ステートメントの実行に権限は必要ありませんが、 EXECUTE 文字列内で参照されるセキュリティ保護可能なリソースに対しては権限が**必要です**。 たとえば、この文字列に [INSERT](https://msdn.microsoft.com/library/ms174335.aspx) ステートメントが含まれている場合、EXECUTE ステートメントの呼び出し元は対象のテーブルに対する INSERT 権限が必要です。 EXECUTE ステートメントは、モジュール内に含まれている場合でも、検出されるたびに権限が確認されます。 詳細については、「[EXECUTE &#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md)」を参照してください。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
### 例 
  
この例では、`AdventureWorks` のほとんどのエディションで利用できる `ufnGetSalesOrderStatusText` スカラー値関数を使用しています。  この関数の目的は、所与の整数から売り上げ状況のテキスト値を返すことです。  **\@Status** パラメーターに 1 ～ 7 の整数を渡すことで例を変えられます。
  
~~~tsql
USE [AdventureWorks2016CTP3]
GO  

-- Declare a variable to return the results of the function. 
DECLARE @ret nvarchar(15);   

-- Execute the function while passing a value to the @status parameter
EXEC @ret = dbo.ufnGetSalesOrderStatusText 
    @Status = 5; 

-- View the returned value.  The Execute and Select statements must be executed at the same time.  
SELECT N'Order Status: ' + @ret; 

-- Result:
-- Order Status: Shipped
~~~
  
  
  