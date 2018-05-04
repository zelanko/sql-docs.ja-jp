---
title: スクロール可能なカーソルの種類 |Microsoft ドキュメント
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
- scrollable cursors [ODBC]
- cursors [ODBC], scrollable
ms.assetid: dbd32576-0453-4e90-ae45-1a81cee8259d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 54acbd1010d546649b1ad92a34289fa4d04da162
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="scrollable-cursor-types"></a>スクロール可能なカーソルの種類
次の 4 つの種類のスクロール可能なカーソルは静的、動的、キーセット ドリブン、混合です。 静的カーソルは、ほとんどまたはまったく変更の検出が、比較的負荷の少ないを実装するのには、します。 動的カーソルでは、すべての変更を検出が、実装にコストがかかります。 キーセット ドリブン カーソルと混合カーソルは、動的カーソルよりも少ない経費では、ほとんどの変更を検出する間にあります。  
  
 スクロール可能なカーソルの種類ごとの特性を定義する、次の用語が使用されます。  
  
-   **独自の更新、削除、および挿入します。** 更新、削除、およびへの呼び出しのいずれかと、カーソルによって行われた挿入**SQLBulkOperations**または**SQLSetPos**または位置指定の delete ステートメントまたは更新します。  
  
-   **削除すると、および挿入します。 他の更新します。** 更新、削除、およびいないなど、同じトランザクションでは、その他の操作によって行われた、カーソルによって行われた挿入、他のトランザクションを通じて行われますが、および他のアプリケーションによって行われたものです。  
  
-   **メンバーシップ。** 結果セット内の行のセット。  
  
-   **順序です。** カーソルによって返される行の順序。  
  
-   **値。** 結果セット内の各行の値。  
  
 更新、削除、およびデータを挿入する方法については、次を参照してください。[更新データの概要](../../../odbc/reference/develop-app/updating-data-overview.md)です。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ODBC 静的カーソル](../../../odbc/reference/develop-app/odbc-static-cursors.md)  
  
-   [ODBC 動的カーソル](../../../odbc/reference/develop-app/odbc-dynamic-cursors.md)  
  
-   [キーセット ドリブン カーソル](../../../odbc/reference/develop-app/keyset-driven-cursors.md)  
  
-   [混合カーソル](../../../odbc/reference/develop-app/mixed-cursors.md)
