---
title: 行セットのバインド (ODBC) を使用して |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- rowset binding [ODBC]
ms.assetid: a7be05f0-6b11-4b53-9fbc-501e591eef09
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 2ef6f3651cb1cb1c80247f5853b4d4bd05bc13fc
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2018
ms.locfileid: "35694443"
---
# <a name="use-rowset-binding-odbc"></a>行セットのバインドの使用 (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

    
### <a name="to-use-column-wise-binding"></a>列方向のバインドを使用するには  
  
1.  バインドされた各列で、次の操作を行います。  
  
    -   データ値を格納するための R 個以上の列バッファーの配列を割り当てます。R は行セット内の行の数です。  
  
    -   必要に応じて、データ長を格納するための R 個以上の列バッファーの配列を割り当てます。  
  
    -   呼び出す[SQLBindCol](../../../relational-databases/native-client-odbc-api/sqlbindcol.md)行セットの列に列のデータ値とデータの長さの配列をバインドします。  
  
2.  呼び出す[SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)を次の属性を設定します。  
  
    -   SQL_ATTR_ROW_ARRAY_SIZE を、行セットの行の数 (R) に設定します。  
  
    -   SQL_ATTR_ROW_BIND_TYPE を SQL_BIND_BY_COLUMN に設定します。  
  
    -   SQL_ATTR_ROWS FETCHED_PTR 属性を、フェッチされた行の数を格納する SQLUINTEGER 変数を指すように設定します。  
  
    -   SQL_ATTR_ROW_STATUS_PTR を、行状態インジケーターを格納する SQLUSSMALLINT 変数の配列 [R] を指すように設定します。  
  
3.  ステートメントを実行します。  
  
4.  各呼び出し[SQLFetch](http://go.microsoft.com/fwlink/?LinkId=58401)または[SQLFetchScroll](../../../relational-databases/native-client-odbc-api/sqlfetchscroll.md) R 行を取得し、バインドされた列にデータを転送します。  
  
### <a name="to-use-row-wise-binding"></a>行方向のバインドを使用するには  
  
1.  構造体の配列 [R] を割り当てます。この R は行セット内の行数です。 構造体には各列について 1 つの要素があり、各要素は 2 つの部分で構成されています。  
  
    -   最初の部分は、列データを格納する適切なデータ型の変数です。  
  
    -   2 つ目の部分は、列状態インジケーターを格納する SQLINTEGER 変数です。  
  
2.  呼び出す[SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)を次の属性を設定します。  
  
    -   SQL_ATTR_ROW_ARRAY_SIZE を、行セットの行の数 (R) に設定します。  
  
    -   SQL_ATTR_ROW_BIND_TYPE を、手順 1. で割り当てた構造体のサイズに設定します。  
  
    -   SQL_ATTR_ROWS_FETCHED_PTR 属性を、フェッチされた行の数を格納する SQLUINTEGER 変数を指すように設定します。  
  
    -   SQL_ATTR_PARAMS_STATUS_PTR を、行状態インジケーターを格納する SQLUSSMALLINT 変数の配列 [R] を指すように設定します。  
  
3.  結果セット内の各列を呼び出して[SQLBindCol](../../../relational-databases/native-client-odbc-api/sqlbindcol.md)に手順 1. で割り当てた構造体の配列の最初の要素にある変数をデータ値と列のデータ長のポインターをポイントします。  
  
4.  ステートメントを実行します。  
  
5.  各呼び出し[SQLFetch](http://go.microsoft.com/fwlink/?LinkId=58401)または[SQLFetchScroll](../../../relational-databases/native-client-odbc-api/sqlfetchscroll.md) R 行を取得し、バインドされた列にデータを転送します。  
  
## <a name="see-also"></a>参照  
 [カーソルの操作方法に関するトピックを使用して&#40;ODBC&#41;](../../../relational-databases/native-client-odbc-how-to/cursors/using-cursors-how-to-topics-odbc.md)   
 [カーソルの実装方法](../../../relational-databases/native-client-odbc-cursors/implementation/how-cursors-are-implemented.md)   
 [カーソルを使用して&#40;ODBC&#41;](../../../relational-databases/native-client-odbc-how-to/cursors/use-cursors-odbc.md)  
  
  
