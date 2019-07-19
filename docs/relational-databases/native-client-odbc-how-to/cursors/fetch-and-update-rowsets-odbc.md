---
title: フェッチおよび更新行セット (ODBC) |マイクロソフトのドキュメント
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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: bb0055e8ed8c17679c824fdf6cbf96c1a42c7531
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67939584"
---
# <a name="fetch-and-update-rowsets-odbc"></a>行セットのフェッチおよび更新 (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

    
### <a name="to-fetch-and-update-rowsets"></a>行セットをフェッチおよび更新するには  
  
1.  必要に応じて、呼び出す[SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) sql_row_array_size (R)、行セット内の行の数の変更を使用して使用します。  
  
2.  呼び出す[SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401)または[SQLFetchScroll](../../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)行セットを取得します。  
  
3.  バインドされた列が使用されている場合は、行セットのバインドされた列のバッファーでデータ値とデータの長さが使用できるようになります。  
  
     行の呼び出しごとに、バインドされていない列が使用かどうか[SQLSetPos](https://go.microsoft.com/fwlink/?LinkId=58407) SQL_POSITION、カーソルの位置を設定するとして、その各非バインド列。  
  
    -   呼び出す[SQLGetData](../../../relational-databases/native-client-odbc-api/sqlgetdata.md)データを取得する 1 つまたは複数回は、最後の行セットの列バインドされた列をバインド解除されました。 呼び出す[SQLGetData](../../../relational-databases/native-client-odbc-api/sqlgetdata.md)の列番号の昇順にする必要があります。  
  
    -   [SQLGetData](../../../relational-databases/native-client-odbc-api/sqlgetdata.md) を複数回呼び出して、text または image 列からデータを取得します。  
  
4.  実行時データ text または image 列をセットアップします。  
  
5.  呼び出す[SQLSetPos](https://go.microsoft.com/fwlink/?LinkId=58407)または[SQLBulkOperations](https://go.microsoft.com/fwlink/?LinkId=58398)カーソルの位置を設定するには、更新、更新、削除、または行セット内の行を追加します。  
  
     実行時データ text または image 列が更新または追加操作に使用されている場合は、それらの列を処理します。  
  
6.  必要に応じて、カーソル名を指定する、位置指定更新または削除ステートメントを実行 (から使用可能な[SQLGetCursorName](../../../relational-databases/native-client-odbc-api/sqlgetcursorname.md)) と同じ接続上で別のステートメント ハンドルを使用します。  
  
## <a name="see-also"></a>関連項目  
 [カーソルの操作方法に関するトピックを使用して&#40;ODBC&#41;](../../../relational-databases/native-client-odbc-how-to/cursors/using-cursors-how-to-topics-odbc.md)  
  
  
