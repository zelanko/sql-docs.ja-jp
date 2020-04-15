---
title: 行のスクロールとフェッチ (ODBC) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- scrollable cursors [ODBC]
- fetches [ODBC], scrollable cursors
- cursors [ODBC], scrollable
- scrolling rows [ODBC]
ms.assetid: c43764cb-5841-4b89-9dc0-984a7488b3c1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 72d262bf73e69388f65ff281e62235d2d831669e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304203"
---
# <a name="scrolling-and-fetching-rows-odbc"></a>行のスクロールとフェッチ (ODBC)
スクロール可能なカーソルを使用する場合、アプリケーションは**SQLFetchScroll**を呼び出してカーソルを配置し、行をフェッチします。 **SQLFetchScroll**は、相対スクロール (次、前、および相対*n*行) 、絶対スクロール (最初、最後、および行*n)、* およびブックマークによる配置をサポートします。 次の図に示すように **、SQLFetchScroll**のフェッチ*オリエンテーション*と*フェッチ オフセット*引数は、フェッチする行セットを指定します。  
  
 ![次、前、最初、および最後の行セットのフェッチ](../../../odbc/reference/develop-app/media/pr20_2.gif "pr20_2")  
  
 **次、前、最初、および最後の行セットのフェッチ**  
  
 ![絶対的行セット、相対的行セット、およびブックマーク付き行セットのフェッチ](../../../odbc/reference/develop-app/media/pr20_1.gif "pr20_1")  
  
 **絶対行セット、相対行セット、およびブックマークされた行セットのフェッチ**  
  
 **SQLFetchScroll は**、指定された行にカーソルを配置し、その行で始まる行セットの行を返します。 指定された行セットが結果セットの末尾と重なる場合は、部分的な行セットが返されます。 指定された行セットが結果セットの先頭と重なる場合、通常は結果セットの最初の行セットが返されます。詳細については[、SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)関数の説明を参照してください。  
  
 アプリケーションがデータを取得せずにカーソルを配置したい場合もあります。 たとえば、行が存在するかどうかをテストしたり、ネットワーク上に他のデータを持ち込まずに行のブックマークを取得したりできます。 これを行うには、SQL_ATTR_RETRIEVE_DATAステートメント属性をSQL_RD_OFFに設定します。 このステートメント属性の設定に関係なく、ブックマーク列にバインドされた変数 (存在する場合) は常に更新されます。  
  
 行セットが取得された後、アプリケーションは**SQLSetPos**を呼び出して行セット内の特定の行に位置付けるか、行セット内の行を更新できます。 **SQLSetPos**の使用の詳細については、「 [SQLSetPos を使用したデータの更新](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md)」を参照してください。  
  
> [!NOTE]  
>  スクロールは ODBC 2 でサポートされています。*x*ドライバーを**使用して、SQLExtendedFetch**を使用します。 詳細については、「付録 G: 下位互換性のためのドライバガイドライン」の[「ブロック カーソル、スクロール可能なカーソル、および後方互換性](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md)」を参照してください。
