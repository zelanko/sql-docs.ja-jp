---
title: "ブックマークでスクロール |Microsoft ドキュメント"
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
- result sets [ODBC], bookmarks
- bookmarks [ODBC]
- scrolling rows [ODBC]
ms.assetid: 4862f098-41a4-4bd2-894e-f71bb97f9bc0
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e4fbccc07d1b3cf5491f95b57f5e4bb4d2c95f5c
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="scrolling-by-bookmark"></a>ブックマークでスクロール
持つ行をフェッチするときに**SQLFetchScroll**アプリケーションは、開始行を選択するため、基準としてブックマークを使用することができます。 これは、現在のカーソルの位置に依存しないので、絶対アドレスの形式になります。 アプリケーションの呼び出し、ブックマークが付けられた行にスクロールする**SQLFetchScroll**で、 *FetchOrientation* SQL_FETCH_BOOKMARK のです。 この操作は、SQL_ATTR_FETCH_BOOKMARK_PTR ステートメント属性によって示されるブックマークを使用します。 結果として、そのブックマークによって識別される行で始まる行セットが返されます。 アプリケーションにこの操作のオフセットを指定することができます、 *FetchOffset*への呼び出しの引数**SQLFetchScroll**です。 内の数値を追加することで返された行セットの最初の行が決定されますのオフセットを指定すると、 *FetchOffset*ブックマークによって識別される行の数の引数。 このように使用する、 *FetchOffset* ODBC 2 を使用すると、引数がサポートされていません*。x*ドライバー以外の場合は、アプリケーションを呼び出すと**SQLFetchScroll** ODBC 2 *。x*ドライバーと*FetchOrientation*に sql_fetch_bookmark を指定して、設定、 *FetchOffset*引数を 0 に設定する必要があります。
