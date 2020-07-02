---
title: ステートメントハンドルを解放する |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- reusing statement handles
- freeing statement handles
- statements [ODBC], statement handles
- SQLFreeStmt function
- ODBC applications, statements
- statement handles [ODBC]
ms.assetid: 96fdff84-0ca7-460a-a240-94ee826ea41c
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4f1ddc7e81904a9d2224025f521c304a27e10d4b
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85730310"
---
# <a name="freeing-a-statement-handle"></a>ステートメント ハンドルの解放
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  ステートメント ハンドルは、削除して新しいハンドルを割り当てるよりも、再利用する方が効率的です。 アプリケーションでは、任意のステートメント ハンドルで新しい SQL ステートメントを実行する前に、現在のステートメント設定が適切であることを確認する必要があります。 確認する設定には、ステートメント属性、パラメーター バインド、結果セットのバインドがあります。 通常、古い SQL ステートメントのパラメーターと結果セットは、SQL_RESET_PARAMS と SQL_UNBIND のオプションで[SQLFreeStmt](../../relational-databases/native-client-odbc-api/sqlfreestmt.md)を呼び出し、新しい sql ステートメントに対して再バインドすることによって、バインドを解除する必要があります。  
  
 ステートメントを使用してアプリケーションが終了すると、 [Sqlfreehandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md)を呼び出してステートメントを解放します。 **Sqldisconnect**は、接続上のすべてのステートメントを自動的に解放することに注意してください。  
  
## <a name="see-also"></a>関連項目  
 [ODBC&#41;&#40;クエリの実行](../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
  
