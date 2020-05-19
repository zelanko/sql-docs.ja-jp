---
title: 行セットのフェッチおよび更新 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- rowsets [ODBC]
ms.assetid: cf0eb3b4-8b72-49fc-a845-95edc360cf93
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: a799e2c4c7c3e7e3119fece847cb726751441c39
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82701878"
---
# <a name="fetch-and-update-rowsets-odbc"></a>行セットのフェッチおよび更新 (ODBC)
    
### <a name="to-fetch-and-update-rowsets"></a>行セットをフェッチおよび更新するには  
  
1.  必要に応じて、SQL_ROW_ARRAY_SIZE を指定して[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)を呼び出し、行セット内の行数 (R) を変更します。  
  
2.  [Sqlfetch](https://go.microsoft.com/fwlink/?LinkId=58401)または[sqlfetchscroll](../../native-client-odbc-api/sqlfetchscroll.md)を呼び出して、行セットを取得します。  
  
3.  バインドされた列が使用されている場合は、行セットのバインドされた列のバッファーでデータ値とデータの長さが使用できるようになります。  
  
     バインドされていない列を使用する場合は、行ごとに[SQLSetPos](https://go.microsoft.com/fwlink/?LinkId=58407)を呼び出し、カーソル位置を設定するために SQL_POSITION を使用します。次に、バインド解除した列ごとに、次のようにします。  
  
    -   [SQLGetData](../../native-client-odbc-api/sqlgetdata.md)を1回以上呼び出して、行セットの最後にバインドされた列の後にバインドされていない列のデータを取得します。 [SQLGetData](../../native-client-odbc-api/sqlgetdata.md)の呼び出しは、列番号の昇順にする必要があります。  
  
    -   [SQLGetData](../../native-client-odbc-api/sqlgetdata.md) を複数回呼び出して、text または image 列からデータを取得します。  
  
4.  実行時データ text または image 列をセットアップします。  
  
5.  [SQLSetPos](https://go.microsoft.com/fwlink/?LinkId=58407)または[sqlbulkoperations](https://go.microsoft.com/fwlink/?LinkId=58398)を呼び出して、行セット内のカーソル位置の設定、更新、更新、削除、または行の追加を行います。  
  
     実行時データ text または image 列が更新または追加操作に使用されている場合は、それらの列を処理します。  
  
6.  必要に応じて、位置指定の UPDATE または DELETE ステートメントを実行して、カーソル名 ( [Sqlgetcursor name](../../native-client-odbc-api/sqlgetcursorname.md)から使用可能) を指定し、同じ接続で別のステートメントハンドルを使用します。  
  
## <a name="see-also"></a>参照  
 [カーソルの使用方法に関するトピック &#40;ODBC&#41;](using-cursors-how-to-topics-odbc.md)  
  
  
