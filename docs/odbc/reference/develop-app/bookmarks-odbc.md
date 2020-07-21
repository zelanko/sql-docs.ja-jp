---
title: ブックマーク (ODBC) |Microsoft Docs
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
ms.assetid: 1d7cccc5-f847-4321-b240-28570854ee5c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e8273c82b918024417e613ea44a2d26bafaf7d76
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306323"
---
# <a name="bookmarks-odbc"></a>ブックマーク (ODBC)
ブックマークは、データ行の識別に使われる値です。 ブックマーク値の意味を解釈できるのは、ドライバーまたはデータ ソースのみです。 たとえば、ブックマークは、行番号のような単純な値の場合も、ディスク アドレスのような複雑な値の場合もあります。 ODBC のブックマークは、実際のブックのブックマークとは少し異なります。 実際の本では、リーダーは特定のページにブックマークを配置し、そのブックマークを検索してページに戻ります。 ODBC では、アプリケーションが特定の行のブックマークを要求し、これを保存し、カーソルに戻して行に返します。 したがって、ODBC のブックマークは、ページ番号を書き留め、それを記憶し、ページをもう一度検索するリーダーに似ています。  
  
 アプリケーションでは、ドライバーのブックマークのサポートを確認するために、SQL_BOOKMARK_PERSISTENCE オプションを使用して**SQLGetInfo**を呼び出します。 この値のビットは、カーソルが閉じられた後もブックマークが有効であるかどうかなど、操作ブックマークをどのように維持するかを示します。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ブックマークの種類](../../../odbc/reference/develop-app/bookmark-types.md)  
  
-   [ブックマークの取得](../../../odbc/reference/develop-app/retrieving-bookmarks.md)  
  
-   [ブックマークによるスクロール](../../../odbc/reference/develop-app/scrolling-by-bookmark.md)  
  
-   [ブックマークによる更新、削除、またはフェッチ](../../../odbc/reference/develop-app/updating-deleting-or-fetching-by-bookmark.md)  
  
-   [ブックマークの比較](../../../odbc/reference/develop-app/comparing-bookmarks.md)
