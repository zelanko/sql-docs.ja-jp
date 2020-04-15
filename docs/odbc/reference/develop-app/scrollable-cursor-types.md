---
title: スクロール可能なカーソルの種類 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- scrollable cursors [ODBC]
- cursors [ODBC], scrollable
ms.assetid: dbd32576-0453-4e90-ae45-1a81cee8259d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 63f29269ea209875a2e775cf8d523302fcb9a976
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304233"
---
# <a name="scrollable-cursor-types"></a>スクロール可能なカーソルの種類
スクロール可能なカーソルの 4 つのタイプは、静的、動的、キーセット駆動、および混合です。 静的カーソルは、ほとんどまたはまったく変更を検出しませんが、比較的低い方法で実装できます。 動的カーソルはすべての変更を検出しますが、実装にはコストがかかります。 キーセット駆動カーソルと混合カーソルは、ほとんどの変更を検出しますが、動的カーソルよりもコストが少なくなります。  
  
 次の用語は、スクロール可能なカーソルの各タイプの特性を定義するために使用されます。  
  
-   **自身の更新、削除、挿入。** **SQLBulkOperations**または**SQLSetPos**の呼び出し、または位置指定された更新または削除ステートメントを使用して、カーソルを介して行われた更新、削除、および挿入。  
  
-   **その他の更新、削除、挿入。** 同じトランザクション内の他の操作によって行われた操作、他のトランザクションを介して行われた操作、および他のアプリケーションによって行われた操作を含め、カーソルによって行われなかった更新、削除、および挿入。  
  
-   **メンバーシップ。** 結果セット内の行のセット。  
  
-   **順序。** カーソルによって行が返される順序。  
  
-   **値。** 結果セットの各行の値。  
  
 データの更新、削除、挿入の方法については、「データ[の更新の概要](../../../odbc/reference/develop-app/updating-data-overview.md)」を参照してください。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ODBC 静的カーソル](../../../odbc/reference/develop-app/odbc-static-cursors.md)  
  
-   [ODBC 動的カーソル](../../../odbc/reference/develop-app/odbc-dynamic-cursors.md)  
  
-   [キーセット ドリブン カーソル](../../../odbc/reference/develop-app/keyset-driven-cursors.md)  
  
-   [混合カーソル](../../../odbc/reference/develop-app/mixed-cursors.md)
