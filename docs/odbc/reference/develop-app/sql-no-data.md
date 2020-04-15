---
title: SQL_NO_DATA |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL_NO_DATA [ODBC]
- application upgrades [ODBC], SQL_NO_DATA
- backward compatibility [ODBC], SQL_NO_DATA
- compatibility [ODBC], SQL_NO_DATA
- upgrading applications [ODBC], SQL_NO_DATA
ms.assetid: 07a4144a-a548-4578-b2be-715c3cf73bf8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9a399a270eb1cd2f3daf9449c53b1f577a6b9545
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299792"
---
# <a name="sql_no_data"></a>SQL_NO_DATA
ODBC 3 のとき。*x*アプリケーションは、ODBC 2 で**SQLExecDirect** **、SQL 実行**、または**SQL パラム データ**を呼び出します。x*ドライバは*、データ ソースの行に影響を与えない検索された更新または削除ステートメントを実行するには、ドライバはSQL_NO_DATAではなく、SQL_SUCCESSを返す必要があります。 ODBC 2 の場合。*x*または ODBC 3。*x*アプリケーションは ODBC 3 で動作します。*x*ドライバーは、同じ結果、ODBC 3 を使用して**SQLExecDirect** **、SQL 実行**、または**SQLParamData**を呼び出します。*x*ドライバはSQL_NO_DATA返すはずです。
