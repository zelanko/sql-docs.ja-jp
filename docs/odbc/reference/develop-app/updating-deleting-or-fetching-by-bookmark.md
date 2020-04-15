---
title: ブックマークによる更新、削除、またはフェッチ |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- updating by bookmarks [ODBC]
- result sets [ODBC], bookmarks
- fetches [ODBC], by bookmarks [ODBC]
- deleting by bookmarks [ODBC]
- bookmarks [ODBC]
ms.assetid: e2ee58d7-c28f-435f-b537-06207215dd2f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5e94a98bb577ef906afbb04539761fd07d15f772
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286152"
---
# <a name="updating-deleting-or-fetching-by-bookmark"></a>ブックマークによる更新、削除、またはフェッチ
ブックマークを使用すると、結果セット内で更新するデータ、結果セットから削除するデータ、または結果セットから行セット バッファにフェッチするデータを識別できます。 これらの操作は、SQL_UPDATE_BY_BOOKMARK、SQL_DELETE_BY_BOOKMARK、またはSQL_FETCH_BY_BOOKMARKの*オプション*引数を指定した**SQLBulkOperations**の呼び出しによって実行されます。 これらの操作で使用されるブックマークは、行セット バッファーの列 0 に格納されます。 ブックマークで更新する場合、結果セット列が更新されるデータは行セット バッファーから取得されます。 詳細については、「 [SQLBulkOperations を使用したデータの更新](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md)」を参照してください。
