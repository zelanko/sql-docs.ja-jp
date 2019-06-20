---
title: ODBC 静的カーソル |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- cursors [ODBC], static
- static cursors [ODBC]
ms.assetid: 28cb324c-e1c3-4b5c-bc3e-54df87037317
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8ddd2b4d998ab2718757db4dd58de6aea8bee05e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62799010"
---
# <a name="odbc-static-cursors"></a>ODBC 静的カーソル
静的カーソルは静的に結果セットが表示されます。 メンバーシップ、順序、または、カーソルを開いた後に結果セットの値に加えられた変更が通常は検出されません。 たとえば、静的カーソルは行と別のアプリケーションをフェッチし、行を更新します。 静的カーソルは、行を変わりません場合を認識する値は、その他のアプリケーションによって行われた変更に関係なく、変更されたできません。  
  
 静的カーソルには、これを行う必要がなくなりますが、独自の更新、削除、および挿入を検出できます。 SQL_STATIC_SENSITIVITY オプションを使用して特定の静的カーソルがこれらの変更を検出するかどうかは報告**SQLGetInfo**します。 静的カーソルは、その他の更新、削除、および挿入を検出することはありません。  
  
 SQL_ATTR_ROW_STATUS_PTR ステートメント属性で指定された行の状態配列では、任意の行の SQL_ROW_SUCCESS や SQL_ROW_SUCCESS_WITH_INFO、SQL_ROW_ERROR を含めることができます。 更新、削除、またはカーソルがこのような変更を検出できると仮定すると、カーソルによって挿入された行の SQL_ROW_UPDATED、SQL_ROW_DELETED、または SQL_ROW_ADDED を返します。  
  
 静的カーソルが通常結果セット内の行をロックするかコピーを作成して実装や、スナップショットは、結果のセットします。 行ロックは比較的簡単に実行できますが、同時実行を大幅に減らすことの欠点があります。 コピーを作成すると大きな同時実行し独自の更新、削除、変更を追跡するカーソルを使用し、コピーを変更することで挿入します。 ただし、コピーは高額にして、そのデータが他のユーザーによって変更されると、基になるデータから異なることができます。
