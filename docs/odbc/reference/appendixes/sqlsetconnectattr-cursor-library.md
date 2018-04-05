---
title: SQLSetConnectAttr (カーソル ライブラリ) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQLSetConnectAttr function [ODBC], Cursor Library
ms.assetid: 6f70bbd0-a057-49ef-8b05-4c80b58fc6e6
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3366ae3e16b75ef1fea3f388f66675ca4c717bc2
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="sqlsetconnectattr-cursor-library"></a>SQLSetConnectAttr (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないように、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックの使用、 **SQLSetConnectAttr**カーソル ライブラリ内の関数。 に関する一般的な情報**SQLSetConnectAttr**を参照してください[SQLSetConnectAttr 関数](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)です。  
  
 アプリケーションが呼び出す**SQLSetConnectAttr** SQL_ATTR_ODBC_CURSORS 属性をカーソル ライブラリが常に使用になっていること、ドライバーは、スクロール可能なカーソルをサポートしていない場合に使用または使用されないかどうかを指定します。 カーソル ライブラリは、ドライバーでは、SQL_CA1_RELATIVE で SQL_STATIC_CURSOR_ATTRIBUTES1 情報の種類を返す場合に、スクロール可能なカーソルがサポートしている前提としています。 **SQLGetInfo**です。  
  
 アプリケーションを呼び出す必要があります**SQLSetConnectAttr**呼び出された後に、カーソル ライブラリの使用法を指定する**SQLAllocHandle**で、 *HandleType*割り当てるを sql_handle_dbc としての接続およびデータ ソースに接続する前にします。 アプリケーションを呼び出す場合**SQLSetConnectAttr** SQL_ATTR_ODBC_CURSORS 属性を持つ接続がアクティブであるときに、カーソル ライブラリ エラーが返されます。  
  
 接続に関連付けられているすべてのステートメントのカーソル ライブラリでサポートされているステートメント属性を設定するアプリケーションを呼び出す必要があります**SQLSetConnectAttr**とする前に、データ ソースに接続した後は、そのステートメント属性カーソルを開きます。 アプリケーションを呼び出す場合**SQLSetConnectAttr**ステートメントを持つ属性と、カーソルが開いている接続に関連付けられているステートメントで、ステートメント属性は適用されませんそのステートメントにカーソルが閉じられるまで、再度開きます。
