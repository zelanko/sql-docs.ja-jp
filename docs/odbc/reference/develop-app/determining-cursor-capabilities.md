---
title: カーソル機能の決定 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- scrollable cursors [ODBC]
- cursors [ODBC], capabilities
- cursors [ODBC], scrollable
ms.assetid: 35be486c-8f2d-4cec-beb8-df14151abfef
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 984ad8302f2e1695c8df84a64a18042f4cc9e364
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305883"
---
# <a name="determining-cursor-capabilities"></a>カーソル機能の決定
**SQLGetInfo**の次の 4 つのオプションは、サポートされるカーソルの種類とその機能について説明します。  
  
-   SQL_CURSOR_SENSITIVITY。 カーソルが別のカーソルによって行われた変更に影響するかどうかを示します。  
  
-   SQL_SCROLL_OPTIONS。 サポートされているカーソルの種類 (前方専用、静的、キーセット ドリブン、動的、または混合) を一覧表示します。 すべてのデータ ソースは、前方のみのカーソルをサポートする必要があります。  
  
-   SQL_DYNAMIC_CURSOR_ATTRIBUTES1、SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1、SQL_KEYSET_CURSOR_ATTRIBUTES1、またはSQL_STATIC_CURSOR_ATTRIBUTES1 (カーソルのタイプによって異なります)。 スクロール可能なカーソルでサポートされるフェッチタイプをリストします。 戻り値のビットは **、SQLFetchScroll**のフェッチの種類に対応しています。  
  
-   SQL_KEYSET_CURSOR_ATTRIBUTES2またはSQL_STATIC_CURSOR_ATTRIBUTES2 (カーソルのタイプによって異なります)。 静的カーソルとキーセット ドリブン カーソルが、独自の更新、削除、および挿入を検出できるかどうかを示します。  
  
 アプリケーションは、これらのオプションを使用して**SQLGetInfo**を呼び出すことによって、実行時にカーソル機能を決定できます。 これは一般的に汎用アプリケーションによって行われます。 カーソル機能は、アプリケーションの開発中に、アプリケーションにハードコーディングされた機能を決定することもできます。 通常、これは垂直アプリケーションやカスタム アプリケーションで行われますが、ODBC カーソル ライブラリなどのクライアント側カーソル実装を使用する汎用アプリケーションでも実行できます。
