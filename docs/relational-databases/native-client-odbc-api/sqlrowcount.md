---
title: SQL 行数 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLRowCount function
ms.assetid: 967ed3d4-3d31-4485-ac92-027076ebc829
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3cfb76dbd1732e32238c484f589d3b4696ff89d2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302333"
---
# <a name="sqlrowcount"></a>SQLRowCount
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  パラメータ値の配列がステートメント実行にバインドされている場合 **、SQLRowCount**は、パラメータ値のいずれかの行がステートメントの実行時にエラー条件を生成した場合にSQL_ERRORを返します。 関数の*RowCountPtr*引数を使用して値が返されません。  
  
 アプリケーションは、SQL_ATTR_PARAMS_PROCESSED_PTR ステートメント属性を使用して、エラーが発生するまでに処理されたパラメーター数をキャプチャできます。  
  
 また、SQL_ATTR_PARAM_STATUS_PTR ステートメント属性を使用してバインドされた状態値の配列を使用して、問題のあるパラメーター行の配列オフセットをキャプチャできます。 アプリケーションは、状態配列をすべて確認し、実際に処理された行数を判断できます。  
  
 OUTPUT[!INCLUDE[tsql](../../includes/tsql-md.md)]句を指定した INSERT、UPDATE、DELETE、または MERGE ステートメントを実行すると、OUTPUT 句によって生成された結果セット内のすべての行が使用されるまで、SQLRowCount は影響を受ける行の数を返しません。 これらの行を消費するには、SQL フェッチまたは SQL フェッチスクロールを呼び出します。 すべての結果行が使用されるまで、SQLResultCols は -1 を返します。 SQLFetch または SQLFetchScroll がSQL_NO_DATAを返した後、アプリケーションは、次の結果に移動する SQLMoreResults を呼び出す前に、影響を受ける行の数を決定する SQLRowCount を呼び出す必要があります。  
  
## <a name="see-also"></a>参照  
 [関数](https://go.microsoft.com/fwlink/?LinkId=59367)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
