---
title: ODBC スタティック カーソル |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b99566c473e88684e8b092a5ac9fc899e7dce177
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81282448"
---
# <a name="odbc-static-cursors"></a>ODBC 静的カーソル
静的カーソルとは、結果セットが静的であるように見えるカーソルです。 通常、カーソルを開いた後に結果セットのメンバーシップ、順序、または値に加えられた変更は検出されません。 たとえば、静的カーソルが行をフェッチし、別のアプリケーションがその行を更新するとします。 静的カーソルが行を再フェッチする場合、他のアプリケーションによって行われた変更にもかかわらず、そのカーソルが見る値は変更されません。  
  
 静的カーソルは、自身の更新、削除、および挿入を検出できますが、この操作を行う必要はありません。 特定の静的カーソルがこれらの変更を検出するかどうかは **、 SQLGetInfo**の SQL_STATIC_SENSITIVITY オプションを使用して報告されます。 静的カーソルは、他の更新、削除、挿入を検出しません。  
  
 SQL_ATTR_ROW_STATUS_PTR ステートメント属性で指定された行の状態配列には、任意の行のSQL_ROW_SUCCESS、SQL_ROW_SUCCESS_WITH_INFO、またはSQL_ROW_ERRORを含めることができます。 カーソルがこのような変更を検出できると仮定して、カーソルによって更新、削除、または挿入された行に対して、SQL_ROW_UPDATED、SQL_ROW_DELETED、またはSQL_ROW_ADDEDを返します。  
  
 静的カーソルは通常、結果セット内のローをロックするか、結果セットのコピーまたはスナップショットを作成することによって実装されます。 行のロックは比較的簡単ですが、同時実行性を大幅に削減するという欠点があります。 コピーを作成すると、より多くの同時実行性が可能になり、コピーを変更することによってカーソルが自身の更新、削除、および挿入を追跡できます。 ただし、コピーは作成コストが高く、他のデータが変更される場合に基になるデータとは異なる場合があります。
