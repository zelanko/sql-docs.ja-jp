---
title: コマンドの構文 |Microsoft ドキュメント
description: コマンド構文とストアド プロシージャ
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: ole-db-commands
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, commands
- commands [OLE DB]
- OLE DB Driver for SQL Server, stored procedures
- stored procedures [OLE DB], command syntax
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 09c0619e18d1d18d02fd7eddd688c75158fd96f9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="command-syntax"></a>コマンドの構文
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  SQL Server の OLE DB Driver は、DBGUID_SQL マクロで指定されているコマンドの構文を認識します。 OLE DB ドライバーの SQL Server の指定子ことを示します ODBC SQL、ISO の混在と[!INCLUDE[tsql](../../../includes/tsql-md.md)]有効な構文です。 たとえば、次の SQL ステートメントでは、ODBC SQL のエスケープ シーケンスを使用して、LCASE 文字列関数を指定しています。  
  
```  
SELECT customerid={fn LCASE(CustomerID)} FROM Customers  
```  
  
 LCASE 関数は、大文字をすべて小文字に変換した文字列を返します。 ISO の文字列関数 LOWER も同じ操作を実行します。つまり、次の SQL ステートメントは、上記の ODBC ステートメントと同義の ISO ステートメントになります。  
  
```  
SELECT customerid=LOWER(CustomerID) FROM Customers  
```  
  
 SQL Server の OLE DB Driver は、コマンドのテキストとして指定されたときに正常にステートメントのいずれかの形式を処理します。  
  
## <a name="stored-procedures"></a>ストアド プロシージャ  
 実行するときに、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]コマンドは SQL Server、OLE DB ドライバーを使用してストアド プロシージャは、コマンド テキストで、ODBC CALL エスケープ シーケンスを使用します。 SQL Server の OLE DB Driver は、リモート プロシージャ コールのメカニズムを使用して[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]コマンドの処理を最適化します。 たとえば次のような場合、[!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメント形式ではなく、ODBC SQL ステートメントをコマンド テキストとして使用することをお勧めします。  
  
-   ODBC SQL  
  
    ```  
    {call SalesByCategory('Produce', '1995')}  
    ```  
  
-   Transact-SQL  
  
    ```  
    EXECUTE SalesByCategory 'Produce', '1995'  
    ```  
  
## <a name="see-also"></a>参照  
 [[コマンド]](../../oledb/ole-db-commands/commands.md)  
  
  
