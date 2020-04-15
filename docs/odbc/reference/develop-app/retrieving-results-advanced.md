---
title: 結果の取得 (詳細) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- offsets [ODBC]
- result sets [ODBC], about result sets
- bind offsets [ODBC]
ms.assetid: bc00c379-71a7-407a-975c-898243f39bb6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ca02b4ff911c8edff06b38d5341eeaa288cc194c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294642"
---
# <a name="retrieving-results-advanced"></a>結果の取得 (詳細)
アプリケーションは、バインドされたデータ バッファー アドレスにオフセットを追加し **、SQLBulkOperations** **、SQLFetch 、SQLFetchScroll**、**SQLFetchScroll**または**SQLSetPos**が呼び出されたときに、対応する長さ/インジケーター バッファー アドレスを指定できます。 これらの追加の結果は、これらの操作で使用されるアドレスを決定します。  
  
 バインド オフセットを使用すると、アプリケーションは、以前にバインドされた列に対して**SQLBindCol**を呼び出すことなく、バインドを変更できます。 データを再バインドするために**SQLBindCol**を呼び出すと、バッファー・アドレスと長さ/インジケーター・ポインターが変更されます。 一方、オフセットを使用して再バインドすると、既存のバインドされたデータ バッファ アドレスと長さ/インジケーター バッファ アドレスにオフセットが追加されます。 オフセットを使用する場合、バインドはアプリケーション バッファのレイアウト方法の"テンプレート"であり、アプリケーションはオフセットを変更することでこの "テンプレート" をメモリの別の領域に移動できます。 新しいオフセットはいつでも指定でき、常に元のバインド値に追加されます。  
  
 バインド オフセットを指定するために、アプリケーションは、sqlINTEGER バッファーのアドレスにSQL_ATTR_ROW_BIND_OFFSET_PTRステートメント属性を設定します。 アプリケーションが**SQLBulkOperations** **、SQLFetch 、SQLFetchScroll** **SQLFetchScroll** **、SQLSetPos**などのバインディングを使用する関数を呼び出す前に、データ バッファー アドレスも長さ/インジケーター バッファー アドレスも 0 である限り、バインドされた列が結果セット内にある限り、このバッファーにバイト単位でオフセットを配置します。 アドレスとオフセットの合計は、有効なアドレスである必要があります。 (つまり、オフセットの合計が有効なアドレスである限り、オフセットとオフセットを追加するアドレスのいずれかまたは両方が無効になる可能性があります。SQL_ATTR_ROW_BIND_OFFSET_PTRステートメント属性は、オフセット値を複数のバインド・データ・セットに適用できるようにポインターであり、そのすべてが 1 つのオフセット値を変更することによって変更できます。 アプリケーションは、カーソルがクローズされるまで、ポインターが有効であることを確認する必要があります。  
  
> [!NOTE]  
>  バインド オフセットは ODBC 2 ではサポートされていません。*x*ドライバ。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ブロック カーソル](../../../odbc/reference/develop-app/block-cursors.md)  
  
-   [スクロール可能なカーソル](../../../odbc/reference/develop-app/scrollable-cursors.md)  
  
-   [ODBC カーソル ライブラリ](../../../odbc/reference/develop-app/the-odbc-cursor-library.md)  
  
-   [複数の結果](../../../odbc/reference/develop-app/multiple-results.md)
