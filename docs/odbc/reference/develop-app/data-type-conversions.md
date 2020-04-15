---
title: データ型変換 |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cd888fe32692494e2b0ceadc1ed872dd96e244a9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305214"
---
# <a name="data-type-conversions"></a>データ型変換
データは、アプリケーション変数から別のアプリケーション変数にデータが転送されるとき (C から C へ)、アプリケーション変数内のデータがステートメント・パラメーター (C から SQL) に送信される場合、結果セット列のデータがアプリケーション変数 (SQL から C) に戻される場合、およびデータが 1 つのデータ・ソース列から別のデータ・ソース列に転送される (SQL から SQL) の 4 回のいずれかで、あるタイプから別のタイプに変換できます。  
  
 アプリケーション変数間でデータが転送されるときに行われる変換は、このドキュメントの範囲外です。  
  
 アプリケーションが結果セットの列またはステートメント・パラメーターに変数をバインドする場合、アプリケーションは、アプリケーション変数のデータ・タイプの選択でデータ・タイプ変換を暗黙的に指定します。 たとえば、列に整数データが含まれているとします。 アプリケーションが列に整数変数をバインドする場合は、変換を行なわれないことを指定します。アプリケーションが文字変数を列にバインドする場合、データを整数から文字に変換することを指定します。  
  
 ODBC は、各 SQL データ型と C データ型の間でデータを変換する方法を定義します。 基本的に、ODBC は文字から整数、整数から浮動小数点数など、すべての妥当な変換をサポートし、浮動小数点型の変換 (現在までに浮動小数点数など) をサポートしません。 ドライバーは、サポートする各 SQL データ型のすべての変換をサポートする必要があります。 SQL データ型と C データ型の変換の完全な一覧については、「付録 D:[データ型」の「SQL から C データ型へのデータの変換](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)」および[「C から SQL データ型へのデータ変換](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)」を参照してください。  
  
 ODBC では、ある SQL データ型から別のデータ型にデータを変換するためのスカラー関数も定義されています。 **CONVERT**スカラー関数は、ドライバーによって、基になるスカラー関数またはデータ ソースで変換を実行するために定義された関数にマップされます。 この関数は DBMS 固有の関数にマップされるため、ODBC では、これらの変換のしくみやサポートする必要がある変換は定義されません。 アプリケーションは **、SQLGetInfo**のSQL_CONVERT オプションを使用して、特定のドライバーとデータ ソースでサポートされている変換を検出します。 **CONVERT**スカラー関数の詳細については、「 [ODBC のエスケープ シーケンス](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md)」および「[明示的なデータ型変換関数](../../../odbc/reference/appendixes/explicit-data-type-conversion-function.md)」を参照してください。
