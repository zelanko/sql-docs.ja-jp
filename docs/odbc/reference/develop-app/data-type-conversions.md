---
title: データ型の変換 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], conversions
- SQL data types [ODBC], conversions
- converting data [ODBC]
- converting data types [ODBC]
- C data types [ODBC], conversions
ms.assetid: d311fe1c-d882-4136-9fa5-220a4121e04c
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0501e4bf627d8dafddfbf5020345d43135af9d6d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="data-type-conversions"></a>データ型変換
データに変換できる 1 つの型から別に 4 回のいずれかの: 転送するときにデータが 1 つのアプリケーションの変数から間 (C に C)、ステートメントのパラメーター (C から SQL へ) をアプリケーション変数にデータを送信するときに結果セット列のデータが返される場合アプリケーション変数 (SQL から C へ) とときにデータを転送 1 つのデータ ソースの列から (SQL to SQL) のもう 1 つです。  
  
 別のアプリケーションを 1 つの変数からデータを転送するときに発生する変換では、このドキュメントの範囲外です。  
  
 アプリケーションは、結果セットの列またはステートメントのパラメーターに変数をバインドしたときに、アプリケーションはアプリケーション変数のデータ型の選択データ型の変換を暗黙的に指定します。 たとえば、列には、整数型のデータが含まれています。 アプリケーションは、列に整数型の変数をバインドした場合は、変換する実行しないことです。 を指定します。アプリケーションは、列に文字変数をバインドした場合は、文字に整数からデータを変換を指定します。  
  
 ODBC では、それぞれ SQL および C データ型間でデータを変換する方法を定義します。 基本的には、ODBC では、整数および浮動小数点、整数の文字など、すべての適切な変換をサポートし、日付する浮動小数点数など、正しく定義されていない変換をサポートしていません。 ドライバーがサポートする各 SQL データ型のすべての変換をサポートするために必要です。 SQL と C データ型間の変換の一覧については、次を参照してください。[に変換するデータを SQL から C データ型に](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)と[に変換するデータを C から SQL データ型を](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)付録 d: データ型にします。  
  
 ODBC では、データに変換する 1 つの SQL データ型から別のスカラー関数も定義します。 **変換**スカラー関数は、基になるスカラー関数または変換を実行するデータ ソースで定義されている関数へのドライバーによってもマップされます。 この関数が DBMS 固有の関数にマップされているために、これらの変換のしくみや、どのような変換をサポートする必要がありますが ODBC に定義されていません。 アプリケーション検出で SQL_CONVERT オプションによって、特定のドライバーとデータ ソースでどのような変換がサポートされている**SQLGetInfo**です。 詳細については、**変換**スカラー関数を参照してください[odbc エスケープ シーケンス](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md)と[明示的なデータ型変換関数](../../../odbc/reference/appendixes/explicit-data-type-conversion-function.md)です。
