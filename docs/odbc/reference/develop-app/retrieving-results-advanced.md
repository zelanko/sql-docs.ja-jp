---
title: "(詳細) 結果を取得する |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- offsets [ODBC]
- result sets [ODBC], about result sets
- bind offsets [ODBC]
ms.assetid: bc00c379-71a7-407a-975c-898243f39bb6
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 85c3447abebf7ef6eaa538a8a1d5d00edcc007fd
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="retrieving-results-advanced"></a>(詳細) 結果を取得します。
アプリケーションでは、バインドされたデータ バッファーのアドレスおよび対応する長さ/インジケーターにオフセットを追加することを指定できるときにバッファー アドレス**SQLBulkOperations**、 **SQLFetch**、 **SQLFetchScroll**、または**SQLSetPos**と呼びます。 これらの追加の結果は、これらの操作で使用されるアドレスを決定します。  
  
 バインドのオフセットを呼び出さずにバインドを変更するアプリケーションを許可する**SQLBindCol**以前にバインドされた列にします。 呼び出し**SQLBindCol**データを再バインドするバッファーのアドレスと長さ/インジケーターのポインターを変更します。 オフセットを再バインド一方で、単にオフセットを追加、既存のバインドされたデータ バッファーのアドレスと長さ/インジケーター バッファーのアドレス。 オフセットを使用している場合、バインディングは、アプリケーションのバッファーのレイアウトの"template"と、アプリケーションは、オフセットを変更することによってメモリの異なる領域にこの"template"を移動することができます。 新しいオフセットを使用して、いつでもに指定することができますは常に最初にバインドされた値に追加します。  
  
 バインドのオフセットを指定するには、アプリケーションは、SQLINTEGER バッファーのアドレスを SQL_ATTR_ROW_BIND_OFFSET_PTR ステートメント属性を設定します。 アプリケーションなど、バインドを使用する関数を呼び出す前に**SQLBulkOperations**、 **SQLFetch**、 **SQLFetchScroll**、または**SQLSetPos**、オフセットこのバッファー内のバイトのデータ バッファーのアドレスも長さ/インジケーター バッファーのアドレスが 0、限りと配置、バインドされた列が結果セットとして。 アドレスとオフセットの合計は、有効なアドレスである必要があります。 (このいずれかまたは両方オフセットとアドレスのオフセットを追加することができますしないことを示します有効な場合は、その合計が有効なアドレスである限り。)SQL_ATTR_ROW_BIND_OFFSET_PTR ステートメント属性は、1 つのオフセット値を変更することによって変更されたすべてのデータ バインディングの 1 つ以上のセットにオフセット値を適用できるように、ポインターです。 アプリケーションは、カーソルが閉じられるまで、ポインターは有効であることを確認してください。  
  
> [!NOTE]  
>  バインディングのオフセットは、ODBC 2 ではサポートされていません。*x*ドライバー。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ブロック カーソル](../../../odbc/reference/develop-app/block-cursors.md)  
  
-   [スクロール可能なカーソル](../../../odbc/reference/develop-app/scrollable-cursors.md)  
  
-   [ODBC カーソル ライブラリ](../../../odbc/reference/develop-app/the-odbc-cursor-library.md)  
  
-   [複数の結果](../../../odbc/reference/develop-app/multiple-results.md)
