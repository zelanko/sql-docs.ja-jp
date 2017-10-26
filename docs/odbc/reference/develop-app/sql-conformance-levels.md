---
title: "SQL への準拠レベル |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- conformance levels [ODBC], SQL
- SQL conformance levels [ODBC]
- data sources [ODBC], conformance levels
- ODBC drivers [ODBC], conformance levels
ms.assetid: 3529df2c-a09b-4c16-9c60-eae7a06d903a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a493a53b736ef5a2606cca1fca710957e30616f1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sql-conformance-levels"></a>SQL への準拠レベル
ドライバーでサポートされている SQL 92 文法のレベルがへの呼び出しによって返される値で示される**SQLGetInfo** SQL_SQL_CONFORMANCE 情報の種類とします。 これは、ドライバーは、sql-92 で定義されているエントリ、FIPS 移行中、中間、またはフル レベルに準拠しているかどうかを示します。  
  
 すべての ODBC ドライバーは、SQL の文法で説明をサポートする必要があります[SQL 文法](../../../odbc/reference/appendixes/sql-minimum-grammar.md)付録 c: SQL の文法でします。 この文法では、SQL 92 エントリ レベルのサブセットです。 ドライバーは、その他の SQL をサポートし、127-2 過渡期レベル、sql-92 エントリ、中間、または完全レベルまたは FIPS に準拠することに可能性があります。 指定されたレベルの SQL 92 または FIPS 127-2 に準拠しているドライバーは、追加機能をサポートしてより高いレベルのいずれかでまだ完全に準拠するレベルにはできません。 機能がサポートされているかどうかを決定するには、アプリケーションを呼び出す必要があります**SQLGetInfo**で適切な情報の種類。 SQL 機能の準拠レベルは、対応する情報の種類の説明です。 (を参照してください、 [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)関数の説明です)。

