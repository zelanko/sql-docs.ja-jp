---
title: 'Sqlclo: |Microsoft Docs'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLCloseCursor function
ms.assetid: e7134d65-5c1c-4ae2-b119-d9b4b9a42483
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 13f863e23b50b1555b5a945111570bacf5486f6e
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: ja-JP
ms.lasthandoff: 07/06/2020
ms.locfileid: "86004388"
---
# <a name="sqlclosecursor"></a>SQLCloseCursor
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  **SqlcloSQLFreeStmt**は、 [SQLFreeStmt](../../relational-databases/native-client-odbc-api/sqlfreestmt.md) *オプション*の値を SQL_CLOSE に置き換えます。 Native Client ODBC ドライバーでは、 **Sqlcloの**受信時に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 保留中の結果セットの行が破棄されます。 ステートメントの列とパラメーターのバインド (存在する場合) は、 **Sqlcloに**よって変更されないことに注意してください。  
  
## <a name="see-also"></a>参照  
 [SQLCloseCursor](https://go.microsoft.com/fwlink/?LinkId=59331)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
