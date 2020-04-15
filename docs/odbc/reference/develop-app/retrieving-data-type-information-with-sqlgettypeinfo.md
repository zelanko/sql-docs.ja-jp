---
title: データ型情報の取得マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL data types [ODBC], identifiers
- SQLGetTypeInfo function [ODBC], retrieving data type information
- retrieving data type information [ODBC]
- type identifiers [ODBC], SQL
- identifiers [ODBC], SQL type
- SQL type identifiers [ODBC]
ms.assetid: d4f8b152-ab9e-4d05-a720-d10a08a6df81
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4ec2bbba824eaf3d74133cf9754eca2593c9fb79
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300062"
---
# <a name="retrieving-data-type-information-with-sqlgettypeinfo"></a>SQLGetTypeInfo によるデータ型情報の取得
基になる SQL データ型から ODBC 型識別子へのマッピングは概算であるため、ODBC には、データ ソース内の各 SQL データ型を完全に記述できる関数 (**SQLGetTypeInfo**) が用意されています。 この関数は、名前、型識別子、精度、小数点以下桁数、NULL 値の許容度など、単一のデータ型の特性を記述する結果セットを返します。  
  
 この情報は、一般に、ユーザーがテーブルを作成および変更できるようにする汎用アプリケーションで使用されます。 このようなアプリケーションは **、SQLGetTypeInfo**を呼び出してデータ型情報を取得し、その一部またはすべてをユーザーに提示します。 このようなアプリケーションは、次の 2 つの点に注意する必要があります。  
  
-   複数の SQL データ型を単一の型識別子にマップできるため、使用するデータ型を判断するのが困難になる場合があります。 これを解決するために、結果セットは最初に型識別子で並べられ、次に型識別子の定義に近づくと並べられます。 また、データ ソース定義のデータ型は、ユーザー定義のデータ型よりも優先されます。 たとえば、データ ソースが整数型と COUNTER データ型を同じに定義するとしますが、COUNTER が自動インクリメントを行う点を除いては、次の点が異なります。 ユーザー定義型の整数型が整数の同義語であるとします。 これらの各型は、SQL_INTEGERにマップされます。 **結果**セットでは、整数が最初に表示され、次に整数が続き、次にカウンタが表示されます。 整数は、ユーザー定義であるため、整数の後に表示されますが、COUNTER の前に、SQL_INTEGER型識別子の定義と一致するためです。  
  
-   ODBC では **、CREATE TABLE**ステートメントおよび ALTER **TABLE**ステートメントで使用するデータ型名は定義されません。 代わりに、アプリケーションは**SQLGetTypeInfo**によって返される結果セットのTYPE_NAME列に返される名前を使用する必要があります。 その理由は、ほとんどの SQL は DBMS 間で大きく異なるわけではありませんが、データ型名は大きく異なっているためです。 ドライバーに SQL ステートメントの解析を強制し、標準のデータ型名を DBMS 固有のデータ型名に置き換えるのではなく、ODBC では、アプリケーションが DBMS 固有の名前を使用する必要があります。  
  
 **SQLGetTypeInfo**は、アプリケーションが発生する可能性のあるすべてのデータ型を必ずしも記述しないことに注意してください。 特に、結果セットには、データ ソースで直接サポートされていないデータ型が含まれている場合があります。 たとえば、カタログ関数によって返される結果セットの列のデータ型は ODBC によって定義され、これらのデータ型はデータ ソースでサポートされない場合があります。 結果セット内のデータ型の特性を判断するために、アプリケーションは**SQLColAttribute**を呼び出します。
