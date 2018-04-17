---
title: ODBC の静的カーソル |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cursors [ODBC], static
- static cursors [ODBC]
ms.assetid: 28cb324c-e1c3-4b5c-bc3e-54df87037317
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d3d6810d2cc6ac0ba3eb4125372944c6c96e3ddb
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="odbc-static-cursors"></a>ODBC の静的カーソル
静的カーソルは静的に結果セットが表示されます。 メンバーシップ、順序、または、カーソルが開かれた後に結果セットの値に加えられた変更が通常検出されません。 たとえば、静的カーソルが別のアプリケーションと行をフェッチし、行を更新します。 静的カーソルは、行を変わりません場合に、表示される値は変更されず、他のアプリケーションによって行われた変更に関係なく。  
  
 静的カーソルには、これらは、これを行うには必要ありませんが、独自の更新、削除、および挿入を検出できます。 特定の静的カーソルがこれらの変更を検出するかどうかが SQL_STATIC_SENSITIVITY オプションによって報告された**SQLGetInfo**です。 静的カーソルは、他の更新、削除、および挿入を検出することはありません。  
  
 SQL_ATTR_ROW_STATUS_PTR ステートメント属性によって指定された行の状態配列では、任意の行の SQL_ROW_SUCCESS、SQL_ROW_SUCCESS_WITH_INFO、または SQL_ROW_ERROR を含めることができます。 更新、削除、またはカーソルがこのような変更を検出できると仮定すると、カーソルによって挿入された行の SQL_ROW_UPDATED、SQL_ROW_DELETED、または SQL_ROW_ADDED を返します。  
  
 静的カーソルは通常、コピーを作成または、結果セット内の行をロックによって実装または、スナップショットは、結果セットです。 行ロックを行うには比較的簡単ですが、同時実行制御が大幅に削減の欠点があります。 コピーを作成するとにより、同時実行性に大きくと独自の更新、削除、変更を追跡する、カーソルを使用し、コピーを変更することで挿入します。 ただし、コピーはコストが増大してそのデータが他のユーザーによって変更されると、基になるデータから分岐できます。
