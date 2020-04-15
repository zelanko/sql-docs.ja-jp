---
title: API 関数に関するスレッド セーフに関する注意事項 (Oracle 用 ODBC ドライバ) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], threading
- threading options [ODBC]
- multiple concurrent statements [ODBC]
ms.assetid: f0c9bdfd-f79d-4088-9ecb-afcd8ca7fb73
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 489f0e99ea53d419ff94dddfeb22e37573abb874
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303073"
---
# <a name="thread-safety-notes-on-api-functions-odbc-driver-for-oracle"></a>API 関数 (ODBC Driver for Oracle) のスレッド セーフの注意事項
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 Oracle 用の ODBC ドライバーはスレッド セーフです。ただし、Oracle では、1 つの接続で複数の同時実行ステートメントを使用することはできません。 ドライバーは、この制限を適用します。 つまり、マルチスレッド アプリケーションでは、任意のスレッドがいつでも Oracle 用 ODBC ドライバーを呼び出すことができますが、ドライバーは、元のスレッドがドライバーを終了するまで、同じ接続上のドライバーから他のスレッドをブロックします。  
  
 2 つの異なる接続に 2 つのステートメントがある場合、ドライバーはブロックしません。 ただし、2 つのステートメントを使用する単一の接続がある場合は、ブロックが発生する可能性があります。
