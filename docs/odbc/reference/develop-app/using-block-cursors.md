---
title: ブロック カーソルを使用する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- cursors [ODBC], block
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 2aad7d6b-216e-47e7-b3cb-f95ad096f21a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f5c487bd8b60a83c709399cb9673dc0b015bd79d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306793"
---
# <a name="using-block-cursors"></a>ブロック カーソルの使用
ブロック カーソルのサポートは ODBC 3 に組み込まれています。*x .* **SQLFetch**は、ODBC 3 で呼び出された場合、複数行のフェッチに対してのみ使用できます。*x;* ODBC 2 の場合。*x*アプリケーションは**SQLFetch**を呼び出し、単一行の前方のみのカーソルのみを開きます。 ODBC 3 のとき。*x*アプリケーションは、ODBC 2 で**SQLFetch**を呼び出します。*x*ドライバーは、ドライバーが**SQLExtendedFetch**をサポートしていない限り、1 つの行を返します。 詳細については、「付録 G: 下位互換性のためのドライバガイドライン」の[「ブロック カーソル、スクロール可能なカーソル、および後方互換性](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md)」を参照してください。  
  
 ブロック カーソルを使用するには、アプリケーションは行セットのサイズを設定し、行セット バッファーをバインド (前のセクションで説明したように) 、オプションでSQL_ATTR_ROWS_FETCHED_PTRとSQL_ATTR_ROW_STATUS_PTRステートメント属性を設定し **、SQLFetch**または**SQLFetchScroll**を呼び出して行ブロックをフェッチします。 アプリケーションは、行セットのサイズを変更し、行がフェッチされた後でも **(SQLBindCol**を呼び出すか、バインド オフセットを指定することによって) 新しい行セット バッファーをバインドできます。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [行セット サイズ](../../../odbc/reference/develop-app/rowset-size.md)  
  
-   [フェッチされた行の数と状態](../../../odbc/reference/develop-app/number-of-rows-fetched-and-status.md)  
  
-   [カーソルをブロックします。ブロック・カーソ](../../../odbc/reference/develop-app/sqlgetdata-and-block-cursors.md)
