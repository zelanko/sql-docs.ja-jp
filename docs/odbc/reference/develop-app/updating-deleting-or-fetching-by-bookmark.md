---
title: 更新、削除、またはのブックマークでフェッチ |Microsoft ドキュメント
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
- updating by bookmarks [ODBC]
- result sets [ODBC], bookmarks
- fetches [ODBC], by bookmarks [ODBC]
- deleting by bookmarks [ODBC]
- bookmarks [ODBC]
ms.assetid: e2ee58d7-c28f-435f-b537-06207215dd2f
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 905278d3bb7100f1db05a2dea99ced009d21deb3
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="updating-deleting-or-fetching-by-bookmark"></a>更新、削除、またはブックマークによる行フェッチ
設定、または結果を行セットのバッファー セットからフェッチされた結果から削除された、結果セットに更新するデータを特定するのには、ブックマークを使用できます。 呼び出しによってこれらの操作が実行されます**SQLBulkOperations**で、*オプション*SQL_UPDATE_BY_BOOKMARK、SQL_DELETE_BY_BOOKMARK、または SQL_FETCH_BY_BOOKMARK の引数。 これらの操作で使用されるブックマークは、列 0 の行セットのバッファーに格納されます。 ブックマークを更新するときは、結果セット列のデータが行セットのバッファーから取得したに更新されます。 詳細については、次を参照してください。 [SQLBulkOperations でのデータの更新](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md)です。
