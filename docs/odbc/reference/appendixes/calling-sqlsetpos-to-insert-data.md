---
title: データを挿入するための SQLSetPos の呼び出し |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- compatibility [ODBC], SQLSetPos
- SQLSetPos function [ODBC], inserting data
- backward compatibility [ODBC], SqlSetPos
ms.assetid: 03e5c4d0-2bb3-4649-9781-89cab73f78eb
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cb374b2506d55b400207c8f60bdf42bb6bb4065e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306603"
---
# <a name="calling-sqlsetpos-to-insert-data"></a>データを挿入するための SQLSetPos の呼び出し
ODBC *3.x*ドライバーを処理する ODBC *2.x*アプリケーションが、*操作*引数 SQL_ADD を指定して**SQLSetPos**を呼び出すと、ドライバー マネージャーは、この呼び出しを**SQLBulkOperations**にマップしません。 ODBC *3.x*ドライバーは、SQL_ADDを使用して**SQLSetPos**を呼び出すアプリケーションで動作する必要がある場合、ドライバーはその操作をサポートする必要があります。  
  
 SQL_ADDを使用して**SQLSetPos**が呼び出されたときの動作の 1 つの大きな違いは、状態 S6 で呼び出されたときに発生します。 ODBC *2.x*では、状態 S6 の状態がSQL_ADDで**SQLSetPos**が呼び出されたときに、ドライバーは S1010 を返します (カーソルが**SQLFetch**で配置された後)。 ODBC *3.x*では、SQL_ADD操作を*伴*う**SQLBulk 操作**を状態 S6 で呼び出すことができます。 2 つ目の大きな動作の違いは、SQL_ADD*操作*を使用する**SQLBulk 操作**を状態 S5 で呼び出すことができますが、SQL_ADD**操作を**使用した**SQLSetPos**は呼び出せないということです。 ODBC *3.x*で同じ呼び出しで発生する可能性があるステートメント[の遷移については、「付録 B: ODBC 状態遷移テーブル](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md)」を参照してください。
