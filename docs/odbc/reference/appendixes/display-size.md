---
title: "表示サイズ |Microsoft ドキュメント"
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
- display size of data types [ODBC]
- size of data types [ODBC]
- data types [ODBC], display size
- SQL data types [ODBC], column characteristics
ms.assetid: 9f7f766f-2492-463c-aab7-f2476e222042
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3faac66828cdc408f9bd153377a3aefe74b882b0
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="display-size"></a>表示サイズ
列の表示サイズは、文字形式でデータを表示するために必要な文字の最大数です。 次の表では、各 ODBC SQL データ型の表示サイズを定義します。  
  
|SQL 型の識別子|表示サイズ|  
|-------------------------|------------------|  
|すべての文字の種類 [a]|(固定の型) に定義されているか (変数の型) の最大文字形式でデータを表示するために必要な文字数。|  
|SQL_DECIMAL SQL_NUMERIC|2 を加えた数、列の有効桁数 (記号、*精度*、桁の数字と小数点)。 たとえば、NUMERIC(10,3) として定義されている列の表示サイズには 12 です。|  
|SQL_BIT|1 (1 桁)。|  
|SQL_TINYINT|4 (を記号と 3 桁) に署名されている場合、または 3 (3 桁) が署名されていない場合。|  
|SQL_SMALLINT|6 (記号、および 5 桁の数値) が署名されている場合、または 5 (5 桁の数値) が署名されていない場合。|  
|SQL_INTEGER|11 (記号、および 10 桁) に署名されている場合、または 10 (10 進数) が署名されていない場合。|  
|SQL_BIGINT|20 (符号と署名されている場合、19 桁または 20 桁署名されていない場合)。|  
|SQL_REAL|14 (、記号、7 桁の数字、小数点文字*E*符号、および 2 桁の数字)。|  
|SQL_DOUBLE を使用できます。|24 (、記号、15 桁、小数点文字*E*符号、および 3 桁)。|  
|[A] すべてのバイナリ型|定義済みまたは (変数の型) の最大列の長さが 2 を倍です。 (各バイナリ バイトは、2 桁の 16 進数で表されます)。|  
|SQL_TYPE_DATE|10 (形式の日付*yyyy mm dd*)。|  
|SQL_TYPE_TIME|8 (形式の時刻*hh:mm:ss*)<br /><br /> - または -<br /><br /> 9 + *s* (形式の時刻*hh:mm:ss*[.fff...]、場所*s*秒の小数部の有効桁数です)。|  
|SQL_TYPE_TIMESTAMP|19 (内のタイムスタンプを*- yyyy-mm-dd hh:mm:ss*形式)<br /><br /> - または -<br /><br /> 20 + *s* (内のタイムスタンプを*- yyyy-mm-dd hh:mm:ss*[.fff.] 形式で*s*秒の小数部の有効桁数です)。|  
|すべての interval データ型|参照してください[Interval データ型の長さ](../../../odbc/reference/appendixes/interval-data-type-length.md)です。|  
|SQL_GUID|36 (文字数、 *aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee*形式|  
  
 [a] の変数の型の列またはパラメーターの長さを判断できないのは、ドライバー場合、SQL_NO_TOTAL が返されます。

