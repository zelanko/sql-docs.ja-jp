---
title: SQL 準拠レベル |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- conformance levels [ODBC], SQL
- SQL conformance levels [ODBC]
- data sources [ODBC], conformance levels
- ODBC drivers [ODBC], conformance levels
ms.assetid: 3529df2c-a09b-4c16-9c60-eae7a06d903a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 875330ac78588566b4b1c212f7a65d2841127a61
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301383"
---
# <a name="sql-conformance-levels"></a>SQL の適合性レベル
ドライバーでサポートされている SQL-92 文法のレベルは、SQL_SQL_CONFORMANCE情報の種類を使用して**SQLGetInfo**の呼び出しによって返される値によって示されます。 これは、ドライバーがエントリ、FIPS 移行、中間、または完全なレベルに準拠するかどうかを示します、 SQL-92 で定義されています。  
  
 すべての ODBC ドライバーは、「付録 C: [SQL 文法」の「SQL 最小文法](../../../odbc/reference/appendixes/sql-minimum-grammar.md)」で説明されている最小の SQL 文法をサポートする必要があります。 この文法は、SQL-92 のエントリ レベルのサブセットです。 ドライバーは、追加の SQL をサポートし、SQL-92 エントリ、中間レベル、または完全なレベル、または FIPS 127-2 移行レベルに準拠している可能性があります。 特定のレベルの SQL-92 または FIPS 127-2 に準拠するドライバーは、上位レベルの追加機能をサポートできますが、そのレベルに完全に準拠していません。 機能がサポートされているかどうかを判断するには、アプリケーションは、適切な情報の種類を使用して**SQLGetInfo**を呼び出す必要があります。 SQL 機能の準拠レベルは、対応する情報タイプで説明されています。 (関数の説明[を](../../../odbc/reference/syntax/sqlgetinfo-function.md)参照してください。
