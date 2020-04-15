---
title: ブックマークの取得 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- retrieving bookmarks [ODBC]
- result sets [ODBC], bookmarks
- bookmarks [ODBC]
ms.assetid: a34c8f09-b786-4835-a44b-b7294c970aff
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3d146b2fb9bfc0e7294709e971f1b6752dc99ab3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300072"
---
# <a name="retrieving-bookmarks"></a>ブックマークの取得
アプリケーションでブックマークを使用する場合は、ステートメントを準備または実行する前に、SQL_ATTR_USE_BOOKMARKSステートメント属性をSQL_UB_VARIABLEに設定する必要があります。 ブックマークの作成と保守は負荷のかかる操作になる可能性があるため、ブックマークはアプリケーションで有効にできる場合にのみ有効にする必要があるためです。  
  
 ブックマークは、結果セットの列 0 として返されます。 アプリケーションがそれらを取得する方法は 3 つあります。  
  
-   結果セットの列 0 をバインドします。 **SQLFetch**または**SQLFetchScroll**は、行セット内の各行のブックマークと、他のバインドされた列のデータを返します。  
  
-   **SQLSetPos**を呼び出して行セット内の行に配置し、列 0 の**SQLGetData**を呼び出します。 ドライバーは、ブックマークをサポートしている場合は、アプリケーションが最後のバインド列の前に他の列の**SQLGetData**を呼び出すことを許可しない場合でも、列 0 の**SQLGetData**を呼び出す機能を常にサポートする必要があります。  
  
-   *呼*び出し**SQLBulk操作**の引数をSQL_ADDに設定し、列 0 をバインドします。 カーソルは、行を挿入し、バインドされたバッファー内の行のブックマークを返します。
