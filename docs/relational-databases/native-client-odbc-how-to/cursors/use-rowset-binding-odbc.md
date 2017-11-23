---
title: "行セットのバインド (ODBC) を使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-how-to
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: rowset binding [ODBC]
ms.assetid: a7be05f0-6b11-4b53-9fbc-501e591eef09
caps.latest.revision: "17"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d1afbe98e2825be95a6c009e5cf8123f4a91af2f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
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
 [使用してカーソルの操作方法に関するトピック &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-how-to/cursors/using-cursors-how-to-topics-odbc.md)   
 [カーソルの実装方法](../../../relational-databases/native-client-odbc-cursors/implementation/how-cursors-are-implemented.md)   
 [カーソルを使用する &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-how-to/cursors/use-cursors-odbc.md)  
  
  
