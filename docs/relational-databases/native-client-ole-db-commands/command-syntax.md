---
title: コマンドの構文 |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, commands
- commands [OLE DB]
- SQL Server Native Client OLE DB provider, stored procedures
- stored procedures [OLE DB], command syntax
ms.assetid: d463d3d7-e5cb-426d-8e92-aa29980356b6
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: c7bf0382463f8877deee8d644fa8e7ff16c243d7
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37432691"
---
# <a name="command-syntax"></a>コマンドの構文
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、DBGUID_SQL マクロで指定されたコマンド構文を認識します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーを指定子が示す ODBC SQL、ISO などのステートメントの混在と[!INCLUDE[tsql](../../includes/tsql-md.md)]は有効な構文です。 たとえば、次の SQL ステートメントでは、ODBC SQL のエスケープ シーケンスを使用して、LCASE 文字列関数を指定しています。  
  
```  
SELECT customerid={fn LCASE(CustomerID)} FROM Customers  
```  
  
 LCASE 関数は、大文字をすべて小文字に変換した文字列を返します。 ISO の文字列関数 LOWER も同じ操作を実行します。つまり、次の SQL ステートメントは、上記の ODBC ステートメントと同義の ISO ステートメントになります。  
  
```  
SELECT customerid=LOWER(CustomerID) FROM Customers  
```  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、コマンドのテキストとして指定されたときに正常にステートメントのいずれかの形式を処理します。  
  
## <a name="stored-procedures"></a>ストアド プロシージャ  
 実行するときに、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ストアド プロシージャを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダー コマンド、コマンド テキストで ODBC CALL エスケープ シーケンスを使用します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのリモート プロシージャ コールのメカニズムを使用し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コマンド処理を最適化します。 たとえば次のような場合、[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメント形式ではなく、ODBC SQL ステートメントをコマンド テキストとして使用することをお勧めします。  
  
-   ODBC SQL  
  
    ```  
    {call SalesByCategory('Produce', '1995')}  
    ```  
  
-   Transact-SQL  
  
    ```  
    EXECUTE SalesByCategory 'Produce', '1995'  
    ```  
  
## <a name="see-also"></a>参照  
 [[コマンド]](../../relational-databases/native-client-ole-db-commands/commands.md)  
  
  
