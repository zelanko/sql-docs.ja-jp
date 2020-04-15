---
title: 行セットのサイズ |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- rowset size [ODBC]
- cursors [ODBC], block
- result sets [ODBC], rowset size
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 60366ae8-175c-456a-ae5e-bdd860786911
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 11b95768934f96e1587b3c570b2510f3c2849239
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304243"
---
# <a name="rowset-size"></a>行セット サイズ
使用する行セットのサイズは、アプリケーションによって異なります。 画面ベースのアプリケーションは、一般に 2 つの方法のいずれかに従います。 1 つ目は、行セットのサイズを画面に表示される行数に設定することです。ユーザーが画面のサイズを変更すると、アプリケーションは行セットのサイズを変更します。 2 つ目は、行セットのサイズを 100 など、より大きな数値に設定して、データ ソースへの呼び出し回数を減らすことです。 アプリケーションは、可能な場合は行セット内でローカルにスクロールし、行セットの外側にスクロールする場合にのみ新しい行をフェッチします。  
  
 レポートなどの他のアプリケーションでは、行セットのサイズを、アプリケーションが処理できる最大行数に設定する傾向があります。 行セットのサイズは、各行のサイズと使用可能なメモリの量によって決まります。  
  
 行セットのサイズは、*属性*引数がSQL_ATTR_ROW_ARRAY_SIZEの**SQLSetStmtAttr**の呼び出しによって設定されます。 アプリケーションは、行セットのサイズを変更したり、行セットの新しいバッファーをバインドしたり **(SQLBindCol**を呼び出すか、バインド オフセットを指定)、行がフェッチされた後でも、またはその両方を行うことができます。 行セットのサイズを変更する場合の影響は、関数によって異なります。  
  
-   **SQLFetch**と**SQLFetchScroll**は、呼び出し時に行セットのサイズを使用して、フェッチする行数を決定します。 ただし、SQL_FETCH_NEXTの*フェッチオリエンテーション*を使用した**SQLFetchScroll**は、前のフェッチの行セットに基づいてカーソルをインクリメントし、現在の行セットのサイズに基づいて行セットをフェッチします。  
  
-   **SQLSetPos は、SQLSetPos**が既に設定されている行セットに対して動作するため、SQLFetch または**SQLSetPos** **SQLFetchScroll**の前の呼び出しの時点で有効になっている行セットのサイズを使用します。 **SQLFetch** **また**、行セットのサイズが変更された後に**SQLBulkOperations**が呼び出された場合、新しい行セット サイズも取り込まれます。  
  
-   **SQLBulkOperations は**、フェッチされた行セットとは独立してテーブルに対して操作を実行するため、呼び出し時に有効な行セット サイズを使用します。
