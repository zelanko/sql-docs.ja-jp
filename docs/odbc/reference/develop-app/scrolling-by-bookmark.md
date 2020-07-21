---
title: ブックマークを使ったスクロール |Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304193"
---
# <a name="scrolling-by-bookmark"></a>ブックマークによるスクロール
**Sqlfetchscroll**を使用して行をフェッチする場合、アプリケーションでは開始行を選択するための基礎としてブックマークを使用できます。 これは、現在のカーソルの位置に依存しないので、絶対アドレスの形式になります。 ブックマークが付けられた行までスクロールするには、アプリケーションは SQL_FETCH_BOOKMARK の*Fetchorientation*を使用して**sqlfetchscroll**を呼び出します。 この操作では、SQL_ATTR_FETCH_BOOKMARK_PTR statement 属性が指すブックマークを使用します。 結果として、そのブックマークによって識別される行で始まる行セットが返されます。 アプリケーションでは、 **Sqlfetchscroll**の呼び出しの*fetchoffset*引数でこの操作のオフセットを指定できます。 オフセットが指定されている場合、返される行セットの最初の行は、ブックマークで識別される行の番号に*Fetchoffset*引数の数値を加算することによって決定されます。 この*Fetchoffset*引数の使用は、ODBC 2 で使用する場合はサポートされていません。*x*ドライバー;アプリケーションが ODBC 2 で**Sqlfetchscroll**を呼び出すとき。*Fetchorientation*が SQL_FETCH_BOOKMARK に設定されている*x*ドライバーは、 *fetchorientation*引数を0に設定する必要があります。
