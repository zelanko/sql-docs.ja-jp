---
title: マッピングの設定を行う |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLSetScrollOptions
ms.assetid: a0fa4510-8891-4a61-a867-b2555bc35f05
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 77050df283b10abd17ba62a48bd366d6c1b3f601
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300502"
---
# <a name="sqlsetscrolloptions-mapping"></a>SQLSetScrollOptions のマッピング
アプリケーションが ODBC *3.x*ドライバを使用して**SQLSetScrollOptions**を呼び出し、ドライバが**SQLSetScrollOptions**をサポートしていない場合は、  
  
```  
SQLSetScrollOptions(StatementHandle, Concurrency, KeysetSize, RowsetSize)  
```  
  
 次のように結果が返されます。  
  
-   への呼び出し  
  
    ```  
    SQLGetInfo(ConnectionHandle, InfoType, InfoValuePtr, BufferLength, StringLengthPtr)  
    ```  
  
     *引数に*次の表のいずれかの値を設定*KeysetSize***します。**  
  
    |*引数*|*インフォタイプ引数*|  
    |---------------------------|-------------------------|  
    |SQL_SCROLL_FORWARD_ONLY|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2|  
    |SQL_SCROLL_STATIC|SQL_STATIC_CURSOR_ATTRIBUTES2|  
    |SQL_SCROLL_KEYSET_DRIVEN|SQL_KEYSET_CURSOR_ATTRIBUTES2|  
    |SQL_SCROLL_DYNAMIC|SQL_DYNAMIC_CURSOR_ATTRIBUTES2|  
    |*引数を*超える値|SQL_KEYSET_CURSOR_ATTRIBUTES2|  
  
     引数*KeysetSize*の値が上記の表にリストされていない場合 **、SQLSetScrollOptions**の呼び出しは SQLSTATE S1107 (行の値が範囲外) を返し、次の手順は実行されません。  
  
     次に、ドライバー マネージャーは **、SQLSetScrollOptions**の*同時実行引数*の値に従って、 **SQLGetInfo**の呼び出しによって返される **InfoValuePtr*値に適切なビットが設定されているかどうかを確認します。  
  
    |*同時実行引数*|*インフォタイプ設定*|  
    |----------------------------|------------------------|  
    |SQL_CONCUR_READ_ONLY|SQL_CA2_READ_ONLY_CONCURRENCY|  
    |SQL_CONCUR_LOCK|SQL_CA2_LOCK_CONCURRENCY|  
    |SQL_CONCUR_ROWVER|SQL_CA2_ROWVER_CONCURRENCY|  
    |SQL_CONCUR_VALUES|SQL_CA2_VALUES_CONCURRENCY|  
  
     *同時実行引数*が上記の表の値のいずれでもない場合 **、SQLSetScrollOptions**の呼び出しは SQLSTATE S1108 (同時実行オプションが範囲外) を返し、次の手順は実行されません。 適切なビット (上記の表に示したように) が **InfoValuePtr*に*同時実行*引数に対応する値のいずれかに設定されていない場合 **、SQLSetScrollOptions**の呼び出しは SQLSTATE S1C00 (ドライバーが実行できません) を返し、次の手順はいずれも実行されません。  
  
-   への呼び出し  
  
    ```  
    SQLSetStmtAttr(StatementHandle, SQL_ATTR_CURSOR_TYPE, ValuePtr, 0)  
    ```  
  
     *\*次*の表の値のいずれかに ValuePtr を設定すると **、SQLSetScrollOptions**の*引数*の値に従います。  
  
    |*引数*|*\*バリュープター*|  
    |---------------------------|------------------|  
    |SQL_SCROLL_FORWARD_ONLY|SQL_CURSOR_FORWARD_ONLY|  
    |SQL_SCROLL_STATIC|SQL_CURSOR_STATIC|  
    |SQL_SCROLL_KEYSET_DRIVEN|SQL_CURSOR_KEYSET_DRIVEN|  
    |SQL_SCROLL_DYNAMIC|SQL_CURSOR_DYNAMIC|  
    |*引数を*超える値|SQL_CURSOR_KEYSET_DRIVEN|  
  
-   への呼び出し  
  
    ```  
    SQLSetStmtAttr(StatementHandle, SQL_ATTR_CONCURRENCY, ValuePtr, 0)  
    ```  
  
     値Ptr を設定して **、SQLSetScrollOptions**の*同時実行*引数 。 * \**  
  
-   **呼**び出しで*引数を引数*として正の値に設定すると、  
  
    ```  
    SQLSetStmtAttr(StatementHandle, SQL_ATTR_KEYSET_SIZE, ValuePtr, 0)  
    ```  
  
     値 Ptr が設定されている*場合*は、引数を引数**として設定します**。 * \**  
  
-   への呼び出し  
  
    ```  
    SQLSetStmtAttr(StatementHandle, SQL_ROWSET_SIZE, ValuePtr, 0)  
    ```  
  
     値 Ptr が設定されている場合は **、SQLSetScrollOptions の引数を行セットサイズに設定します**。 * \** *RowsetSize*  
  
    > [!NOTE]  
    >  ドライバー マネージャーは **、SQLSetScrollOptions**をサポートしていない ODBC *3.x*ドライバーを使用して作業するアプリケーションの**SQLSetScrollOptions**をマップすると、ドライバー マネージャーは、SQL_ATTR_ROW_ARRAY_SIZE ステートメント*RowsetSize*属性ではなく、SQL_ROWSET_SIZE ステートメント**オプションを設定**します。 その結果、SQLFetch または**SQLFetchScroll**の呼び出しによって複数の行をフェッチする場合、アプリケーションで**SQLSetScrollOptions** **を**使用することはできません。 **SQLExtendedFetch**の呼び出しによって複数の行をフェッチする場合にのみ使用できます。
