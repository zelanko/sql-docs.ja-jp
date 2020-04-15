---
title: SQL 実行 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLExecute function
ms.assetid: 4d7db8b6-611f-4fe4-be85-2a407059de45
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8965ce25c009f50e1879084e2c61d66e21419698
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300295"
---
# <a name="sqlexecute"></a>SQLExecute
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  ステートメント属性 SQL_SOPT_SS_PARAM_FOCUSが 0 に設定されていない場合、SQLExecute は SQL_ERRORを返し、SQLSTATE=HY024 と「無効な属性値、SQL_SOPT_SS_PARAM_FOCUS (実行時にゼロである必要があります)」というメッセージを含む診断レコードを生成します。 SQL_SOPT_SS_PARAM_FOCUSの詳細については、「 [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)」を参照してください。  
  
## <a name="remarks"></a>解説  
 テーブル値パラメーターの詳細については、「 [ODBC&#41;&#40;テーブル値パラメーター ](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [実行の実行](https://go.microsoft.com/fwlink/?LinkId=80708)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
