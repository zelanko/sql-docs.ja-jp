---
description: SQLExecDirect
title: SQLExecDirect |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLExecDirect function
ms.assetid: e7c2a5b5-83f4-4c72-9aca-7b9fb4748b11
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5870593158aa49b8025fb634d6b651422a00a1c9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88428264"
---
# <a name="sqlexecdirect"></a>SQLExecDirect
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  ステートメント属性 SQL_SOPT_SS_PARAM_FOCUS が0でない場合、SQLExecDirect は SQL_ERROR を返し、SQLSTATE = HY024 の診断レコードと、"無効な属性値、SQL_SOPT_SS_PARAM_FOCUS (実行時にはゼロでなければなりません)" というメッセージを生成します。 SQL_SOPT_SS_PARAM_FOCUS の詳細については、「 [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)」を参照してください。  
  
 テーブル値パラメーターの詳細については、「 [テーブル値パラメーター &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=80709)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
