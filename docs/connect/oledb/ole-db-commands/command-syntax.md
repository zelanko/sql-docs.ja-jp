---
title: コマンドの構文 |Microsoft ドキュメント
description: コマンド構文とストアド プロシージャ
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-commands
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
ms.openlocfilehash: a3ea215d3596842503517a9485187ba2b1368059
ms.sourcegitcommit: e1bc8c486680e6d6929c0f5885d97d013a537149
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2018
ms.locfileid: "35665752"
---
# <a name="command-syntax"></a>コマンドの構文
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

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
  
  
