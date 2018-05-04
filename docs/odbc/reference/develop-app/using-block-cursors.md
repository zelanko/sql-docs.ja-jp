---
title: ブロック カーソルの使用 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- cursors [ODBC], block
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 2aad7d6b-216e-47e7-b3cb-f95ad096f21a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1bca1bc96ac1c2582bab592a80d65639944e0766
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="using-block-cursors"></a>ブロック カーソルを使用します。
ODBC 3 には、ブロック カーソルのサポートが組み込まれています。*x*です。 **SQLFetch** ODBC 3 で呼び出されると、複数行のフェッチにのみ使用できます*。x*以外の場合は、ODBC 2 *。x*アプリケーション呼び出し**SQLFetch**単一行、順方向専用カーソルだけが開きます。 ODBC 3 時にします。*x*アプリケーション呼び出し**SQLFetch** ODBC 2 *。x*ドライバー、1 つの行を返しますこれには、ドライバーがサポートしていない限り**SQLExtendedFetch**です。 詳細については、次を参照してください。[ブロック カーソル、スクロール可能なカーソル、および下位互換性](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md)旧バージョンとの互換性のための付録 g: ドライバーのガイドライン」にします。  
  
 ブロック カーソルを使用するアプリケーションは行セットのサイズを設定、行セットのバッファー (前のセクションで説明されている) と、必要に応じてセット、SQL_ATTR_ROWS_FETCHED_PTR 属性と SQL_ATTR_ROW_STATUS_PTR ステートメント属性、およびバインド呼び出し**SQLFetch**または**SQLFetchScroll**を行のブロックをフェッチします。 アプリケーションは、行セットのサイズを変更し、新しい行セットのバッファーをバインド (を呼び出して**SQLBindCol**バインド オフセットを指定するか) の行がフェッチされた後もします。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [行セット サイズ](../../../odbc/reference/develop-app/rowset-size.md)  
  
-   [フェッチされた行の数と状態](../../../odbc/reference/develop-app/number-of-rows-fetched-and-status.md)  
  
-   [SQLGetData とブロック カーソルです。ブロック カーソル](../../../odbc/reference/develop-app/sqlgetdata-and-block-cursors.md)
