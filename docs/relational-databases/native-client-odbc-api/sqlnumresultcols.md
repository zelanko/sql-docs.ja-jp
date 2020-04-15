---
title: 結果を返す |マイクロソフトドキュメント
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302383"
---
# <a name="sqlnumresultcols"></a>SQLNumResultCols
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  実行されたステートメントの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]場合、ネイティブ クライアント ODBC ドライバーは、結果セット内の列の数を報告するサーバーを訪問しません。 この場合 **、SQLNumResultCols は**サーバーのラウンドトリップを発生しません。 [SQLDescribeCol](../../relational-databases/native-client-odbc-api/sqldescribecol.md)と[SQLCol 属性](../../relational-databases/native-client-odbc-api/sqlcolattribute.md)と同様に、準備されたステートメントではなく実行済みステートメントで**SQLNumResultCols**を呼び出すと、サーバーラウンドトリップが生成されます。  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントまたはステートメント バッチが複数の結果行セットを返すときは、結果セットの列数を報告する場合、あるセットから別のセットへ結果セットを変更することができます。 **各セットに対して呼**び出す必要があります。 列数が変化すると、アプリケーションでは行の結果をフェッチする前に、データ値を再バインドする必要があります。 複数の結果セットの戻り値の処理の詳細については、 [SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md)を参照してください。  
  
 データベース エンジンの機能強化を開始[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]すると、SQLNumResultCols は期待される結果のより正確な説明を取得できます。 これらのより正確な結果は、以前のバージョンの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]SQLNumResultCols によって返される値とは異なる場合があります。 詳細については、「[メタデータの検出](../../relational-databases/native-client/features/metadata-discovery.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [関数](https://go.microsoft.com/fwlink/?LinkId=59359)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
