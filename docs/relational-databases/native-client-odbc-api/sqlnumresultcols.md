---
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
ms.openlocfilehash: 2b56dad6564bad751829497117cc74553806b244
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81302383"
---
# <a name="sqlnumresultcols"></a>SQLNumResultCols
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  実行されたステートメント[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の場合、NATIVE Client ODBC ドライバーはサーバーにアクセスせず、結果セットの列数を報告しません。 この場合、 **Sqlnumresultcols**ではサーバーのやり取りは行われません。 [SQLDescribeCol](../../relational-databases/native-client-odbc-api/sqldescribecol.md)や[sqlcolattribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md)と同様に、準備されているが実行されていないステートメントで**sqlnumresultcols**を呼び出すと、サーバーのラウンドトリップが生成されます。  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントまたはステートメント バッチが複数の結果行セットを返すときは、結果セットの列数を報告する場合、あるセットから別のセットへ結果セットを変更することができます。 **Sqlnumresultcols**は、セットごとに呼び出す必要があります。 列数が変化すると、アプリケーションでは行の結果をフェッチする前に、データ値を再バインドする必要があります。 複数の結果セットを返す処理の詳細については、「 [Sqlmoreresults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md)」を参照してください。  
  
 以降のデータベースエンジンの機能強化[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]により、SQLNumResultCols は、予期される結果についてより正確な説明を得ることができます。 これらのより正確な結果は、以前のバージョンの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]SQLNumResultCols によって返される値とは異なる場合があります。 詳細については、「[メタデータの検出](../../relational-databases/native-client/features/metadata-discovery.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQLNumResultCols 関数](https://go.microsoft.com/fwlink/?LinkId=59359)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
