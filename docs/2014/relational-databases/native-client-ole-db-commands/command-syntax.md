---
title: コマンド構文 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
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
ms.openlocfilehash: 00ab769ee2051edc499d586ab7d5ee1fa47dd854
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62468219"
---
# <a name="command-syntax"></a>コマンドの構文
  Native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client OLE DB プロバイダーは、DBGUID_SQL マクロで指定されたコマンド構文を認識します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーの場合、指定子は、ODBC SQL、ISO、および[!INCLUDE[tsql](../../includes/tsql-md.md)]の混在が有効な構文であることを示します。 たとえば、次の SQL ステートメントでは、ODBC SQL のエスケープ シーケンスを使用して、LCASE 文字列関数を指定しています。  
  
```  
SELECT customerid={fn LCASE(CustomerID)} FROM Customers  
```  
  
 LCASE 関数は、大文字をすべて小文字に変換した文字列を返します。 ISO の文字列関数 LOWER も同じ操作を実行します。つまり、次の SQL ステートメントは、上記の ODBC ステートメントと同義の ISO ステートメントになります。  
  
```  
SELECT customerid=LOWER(CustomerID) FROM Customers  
```  
  
 Native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client OLE DB プロバイダーは、コマンドのテキストとして指定した場合に、ステートメントのいずれかの形式を正常に処理します。  
  
## <a name="stored-procedures"></a>ストアド プロシージャ  
 Native Client OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider コマンドを使用してストアドプロシージャを実行する場合は、コマンドテキストで ODBC CALL エスケープシーケンスを使用します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 次[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に、Native Client OLE DB プロバイダーは、の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]リモートプロシージャコール機構を使用して、コマンド処理を最適化します。 たとえば次のような場合、[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメント形式ではなく、ODBC SQL ステートメントをコマンド テキストとして使用することをお勧めします。  
  
-   ODBC SQL  
  
    ```  
    {call SalesByCategory('Produce', '1995')}  
    ```  
  
-   Transact-SQL  
  
    ```  
    EXECUTE SalesByCategory 'Produce', '1995'  
    ```  
  
## <a name="see-also"></a>参照  
 [コマンド](commands.md)  
  
  
