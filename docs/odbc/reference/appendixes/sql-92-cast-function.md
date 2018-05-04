---
title: Sql-92 CAST 関数 |Microsoft ドキュメント
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
ms.topic: conceptual
helpviewer_keywords:
- functions [ODBC], SQL-92 functions
- SQL-92 functions [ODBC]
- CAST function [ODBC]
ms.assetid: 982f09e5-8205-41b9-98b3-8f898e24743f
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ce0ff593f8f381efb6d54ea73a8dea04f99823ce
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sql-92-cast-function"></a>Sql-92 CAST 関数
**キャスト**、sql-92 で定義された関数は、**変換**ODBC で定義された関数。 同等の関数の構文は次のとおりです。  
  
```  
{ fn CONVERT (value-exp, data-type) } /* ODBC  
CAST (value-exp AS data-type) /* SQL92  
```  
  
 SQL 92**キャスト**関数ではその他のデータ型に変換できるデータ型が必須です。 (詳細については、SQL 92 仕様を参照してください)。**キャスト**関数は、FIPS 過渡期のレベルでサポートされています。  
  
 アプリケーション サポートの決定できます、**キャスト**次のように機能します。  
  
1.  呼び出す**SQLGetInfo** SQL_SQL_CONFORMANCE 情報の種類とします。 情報の種類の戻り値が SQL_SC_FIPS127_2_TRANSITIONAL、SQL_SC_SQL92_INTERMEDIATE、または SQL_SC_SQL92_FULL の場合、**キャスト**関数はサポートされています。  
  
2.  SQL_SQL_CONFORMANCE 情報の種類の戻り値が SQL_SC_ENTRY_LEVEL または 0 の場合は、呼び出す**SQLGetInfo** SQL_SQL92_VALUE_EXPRESSIONS 情報の種類とします。 SQL_SVE_CAST ビットが設定されている場合、**キャスト**関数はサポートされています。
