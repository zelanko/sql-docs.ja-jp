---
title: データ型の変換 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], conversions
- SQL data types [ODBC], conversions
- converting data [ODBC]
- converting data types [ODBC]
- C data types [ODBC], conversions
ms.assetid: d311fe1c-d882-4136-9fa5-220a4121e04c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 590bd488ae87e8e871837c3055a3225794850d00
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68077013"
---
# <a name="data-type-conversions"></a>データ型変換
データを1つの型から別の型に変換することができます。1つのアプリケーション変数から別のアプリケーション変数 (C から C) にデータを転送するときに、アプリケーション変数のデータがステートメントパラメーター (C から SQL) に送信されるときに、結果セットの列のデータが返されます。アプリケーション変数 (SQL から C)、およびデータがあるデータソース列から別の列に転送されるとき (SQL から SQL)。  
  
 あるアプリケーション変数から別のアプリケーション変数にデータが転送されるときに行われる変換は、このドキュメントの範囲外です。  
  
 アプリケーションで、結果セットの列またはステートメントのパラメーターに変数をバインドすると、アプリケーションは、アプリケーション変数のデータ型を選択して、データ型の変換を暗黙的に指定します。 たとえば、列に整数データが含まれているとします。 アプリケーションで整数変数が列にバインドされている場合は、変換が行われないことを指定します。アプリケーションが文字変数を列にバインドする場合は、データが整数から文字に変換されることを指定します。  
  
 ODBC では、各 SQL データ型と C データ型の間でデータを変換する方法を定義します。 基本的に、ODBC は、文字から整数への変換や float 型の整数など、すべての適切な変換をサポートします。また、float to date など、不適切に定義された変換はサポートしていません。 ドライバーは、サポートする各 SQL データ型のすべての変換をサポートするために必要です。 SQL と C のデータ型の間の変換の完全な一覧については、「付録 D: データ型」の「 [sql から c データ型](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)へのデータの変換」および「 [c から SQL データ型へのデータ](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)の変換」を参照してください。  
  
 ODBC では、SQL データ型間でデータを変換するためのスカラー関数も定義されています。 **CONVERT**スカラー関数は、データソースで変換を実行するために定義されている、基になるスカラー関数または関数にドライバーによってマップされます。 この関数は DBMS 固有の関数にマップされるため、ODBC では、これらの変換のしくみやサポートする必要がある変換を定義していません。 アプリケーションは、 **SQLGetInfo**の SQL_CONVERT オプションを使用して、特定のドライバーとデータソースでサポートされている変換を検出します。 スカラーの**変換**関数の詳細については、「 [ODBC でのエスケープシーケンス](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md)」および「[明示的なデータ型の変換関数](../../../odbc/reference/appendixes/explicit-data-type-conversion-function.md)」を参照してください。
