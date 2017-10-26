---
title: "ブックマーク (ODBC) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- result sets [ODBC], bookmarks
- bookmarks [ODBC]
ms.assetid: 1d7cccc5-f847-4321-b240-28570854ee5c
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 791350c93e2570ad8615e5b378e9979870e02acf
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="bookmarks-odbc"></a>ブックマーク (ODBC)
ブックマークは、データ行の識別に使われる値です。 ブックマーク値の意味を解釈できるのは、ドライバーまたはデータ ソースのみです。 たとえば、ブックマークは、行番号のような単純な値の場合も、ディスク アドレスのような複雑な値の場合もあります。 ODBC でのブックマークは、実際のブック内のブックマークとは少し異なります。 実際の書籍では、リーダーは、特定のページにブックマークを配置し、次に、ページに戻るには、そのブックマークを検索します。 ODBC では、アプリケーションが特定の行のブックマークを要求し、これを保存し、カーソルに戻して行に返します。 したがって、ODBC でのブックマークは、記憶し、もう一度ページを検索し、ページ番号を書き留めるリーダーに似ています。  
  
 ブックマークのドライバーのサポートを確認するには、アプリケーションが呼び出す**SQLGetInfo** SQL_BOOKMARK_PERSISTENCE オプションを使用します。 この値のビットは、どのような操作のブックマークで回収されず、カーソルが閉じられた後にブックマークが現在も有効にはかどうかなどについて説明します。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ブックマークの種類](../../../odbc/reference/develop-app/bookmark-types.md)  
  
-   [ブックマークを取得します。](../../../odbc/reference/develop-app/retrieving-bookmarks.md)  
  
-   [ブックマークでスクロール](../../../odbc/reference/develop-app/scrolling-by-bookmark.md)  
  
-   [更新、削除、またはブックマークによる行フェッチ](../../../odbc/reference/develop-app/updating-deleting-or-fetching-by-bookmark.md)  
  
-   [ブックマークを比較します。](../../../odbc/reference/develop-app/comparing-bookmarks.md)

