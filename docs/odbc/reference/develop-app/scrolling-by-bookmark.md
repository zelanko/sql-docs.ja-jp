---
title: ブックマークでスクロールする |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], bookmarks
- bookmarks [ODBC]
- scrolling rows [ODBC]
ms.assetid: 4862f098-41a4-4bd2-894e-f71bb97f9bc0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 454e29abdf848fdf4f4eaae090e7cc326f0048df
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304193"
---
# <a name="scrolling-by-bookmark"></a>ブックマークによるスクロール
**SQLFetchScroll**を使用して行をフェッチする場合、アプリケーションは開始行を選択するための基礎としてブックマークを使用できます。 これは、現在のカーソルの位置に依存しないので、絶対アドレスの形式になります。 ブックマークされた行にスクロールするには、アプリケーションは、SQL_FETCH_BOOKMARKの*フェッチオリエンテーション*を使用して**SQLFetchScroll**を呼び出します。 この操作では、SQL_ATTR_FETCH_BOOKMARK_PTR ステートメント属性が指すブックマークを使用します。 結果として、そのブックマークによって識別される行で始まる行セットが返されます。 アプリケーションは **、SQLFetchScroll**の呼び出しの*FetchOffset*引数に、この操作のオフセットを指定できます。 オフセットを指定すると、返される行セットの最初の行は、*引数 FetchOffset*の番号をブックマークで識別される行の番号に加算することによって決定されます。 この*FetchOffset*引数の使用は、ODBC 2 で使用する場合はサポートされません。*x*ドライバ。アプリケーションが ODBC 2**で SQLFetchScroll**を呼び出すと、*x*ドライバがSQL_FETCH_BOOKMARK*に設定されている場合**、FetchOffset*引数は 0 に設定する必要があります。
