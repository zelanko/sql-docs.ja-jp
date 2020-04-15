---
title: 行セットのフェッチと更新 (ODBC) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- rowsets [ODBC]
ms.assetid: cf0eb3b4-8b72-49fc-a845-95edc360cf93
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: cec50f99fe5f56c9ce613a8b12c0349823f6f461
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299577"
---
# <a name="fetch-and-update-rowsets-odbc"></a>行セットのフェッチおよび更新 (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

    
### <a name="to-fetch-and-update-rowsets"></a>行セットをフェッチおよび更新するには  
  
1.  必要に応じて、行セット内の行数 (R) を変更するSQL_ROW_ARRAY_SIZEを指定して[SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)を呼び出します。  
  
2.  行セットを取得するには[、SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401)または[SQLFetchScroll](../../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)を呼び出します。  
  
3.  バインドされた列が使用されている場合は、行セットのバインドされた列のバッファーでデータ値とデータの長さが使用できるようになります。  
  
     非バインド列を使用する場合は、行ごとにカーソル位置を設定するSQL_POSITIONを指定して[SQLSetPos](https://go.microsoft.com/fwlink/?LinkId=58407)を呼び出します。次に、各非バインド列について、次の手順を実行します。  
  
    -   行セットの最後のバインド列の後にバインドされていない列のデータを取得するには[、SQLGetData](../../../relational-databases/native-client-odbc-api/sqlgetdata.md)を 1 回以上呼び出します。 [SQLGetData](../../../relational-databases/native-client-odbc-api/sqlgetdata.md)の呼び出しは、列番号を増やす順にする必要があります。  
  
    -   [SQLGetData](../../../relational-databases/native-client-odbc-api/sqlgetdata.md) を複数回呼び出して、text または image 列からデータを取得します。  
  
4.  実行時データ text または image 列をセットアップします。  
  
5.  [SQLSetPos](https://go.microsoft.com/fwlink/?LinkId=58407)または[SQLBulk操作を](https://go.microsoft.com/fwlink/?LinkId=58398)呼び出して、カーソル位置の設定、更新、更新、削除、または行セット内の行の追加を行います。  
  
     実行時データ text または image 列が更新または追加操作に使用されている場合は、それらの列を処理します。  
  
6.  必要に応じて、位置指定された UPDATE ステートメントまたは DELETE ステートメントを実行し、カーソル名[(SQLGetCursorName](../../../relational-databases/native-client-odbc-api/sqlgetcursorname.md)から使用可能) を指定し、同じ接続で別のステートメント ハンドルを使用します。  
  
## <a name="see-also"></a>参照  
 [ODBC&#41;&#40;カーソルの使用方法に関するトピックの使用](../../../relational-databases/native-client-odbc-how-to/cursors/using-cursors-how-to-topics-odbc.md)  
  
  
