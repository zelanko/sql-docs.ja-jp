---
description: SQLNumResultCols
title: SQLNumResultCols |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLNumResultCols function
ms.assetid: f79d8b3c-521e-4e50-a564-21d73ae5767b
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2f4f868d9e32aa553930929cc0f713c9cc29136c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424034"
---
# <a name="sqlnumresultcols"></a>SQLNumResultCols
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  実行されたステートメントの場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC ドライバーはサーバーにアクセスせず、結果セットの列数を報告しません。 この場合、 **Sqlnumresultcols** ではサーバーのやり取りは行われません。 [SQLDescribeCol](../../relational-databases/native-client-odbc-api/sqldescribecol.md)や[sqlcolattribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md)と同様に、準備されているが実行されていないステートメントで**sqlnumresultcols**を呼び出すと、サーバーのラウンドトリップが生成されます。  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントまたはステートメント バッチが複数の結果行セットを返すときは、結果セットの列数を報告する場合、あるセットから別のセットへ結果セットを変更することができます。 **Sqlnumresultcols** は、セットごとに呼び出す必要があります。 列数が変化すると、アプリケーションでは行の結果をフェッチする前に、データ値を再バインドする必要があります。 複数の結果セットを返す処理の詳細については、「 [Sqlmoreresults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md)」を参照してください。  
  
 以降のデータベースエンジンの機能強化により [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 、SQLNumResultCols は、予期される結果についてより正確な説明を得ることができます。 これらのより正確な結果は、以前のバージョンの SQLNumResultCols によって返される値とは異なる場合があり [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 詳細については、「[メタデータの検出](../../relational-databases/native-client/features/metadata-discovery.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQLNumResultCols 関数](https://go.microsoft.com/fwlink/?LinkId=59359)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
