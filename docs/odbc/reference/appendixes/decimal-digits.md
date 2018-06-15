---
title: 10 進数字 |Microsoft ドキュメント
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
- size of data types [ODBC]
- decimal digits of data types [ODBC]
- data types [ODBC], decimal digits
- SQL data types [ODBC], column characteristics
ms.assetid: 07f3d1fc-b4ee-4693-b342-330b2231b6d0
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 307ad06151a821274d376f923a4eb83b37d20622
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32907787"
---
# <a name="decimal-digits"></a>小数点以下桁数
*小数点以下桁数*またはデータの小数点以下桁数、小数点の右側にある数字の最大数として decimal および numeric のデータの種類が定義されています。 浮動小数点概数の数値列またはパラメーターでは、小数点の右側にある数字の数が一定ではないので、小数点以下桁数は定義されません。 Datetime または期間、データの秒の部分を含む 10 進数字は、データの秒の部分の中で小数点の右側にある数字の数として定義されます。  
  
 SQL_DECIMAL および SQL_NUMERIC のデータ型の最大の小数点以下桁数は通常、最大有効桁数と同じです。 ただし、一部のデータ ソース別の制限最大の小数点以下桁数です。 データ型の許容最小値と最大スケールを決定するには、アプリケーションが呼び出す**SQLGetTypeInfo**です。  
  
 次の表に、簡潔な SQL データ型ごとに定義された 10 進数字が表示されます。  
  
|SQL 型|小数点以下桁数|  
|--------------|--------------------|  
|すべての文字とバイナリの種類が [a]|n/a|  
|SQL_DECIMAL<br />SQL_NUMERIC|小数点の右側にある数字の定義済みの数。 たとえば、NUMERIC(10,3) として定義されている列の小数点以下桁数は 3 です。 指数表記を使用せずに非常に多数の記憶域をサポートするために負の数を指定できます。たとえば、「12000」の場合は、–3 の小数点以下桁数には、「12」として格納されている可能性があります。|  
|SQL_DECIMAL と [a] SQL_NUMERIC 以外のすべての正確な数値型|0|  
|すべて概数のデータ型 [a]|n/a|  
|SQL_TYPE_DATE、および秒コンポーネントがありません [a] ですべての間隔の種類|n/a|  
|SQL_TYPE_DATE を除くすべての datetime 型と秒の部分ですべての間隔の種類|値 (秒の小数部) の秒部分の中で小数点の右側にある数字の数。 この数値を負の値にすることはできません。|  
|SQL_GUID|n/a|  
  
 [a]、 *DecimalDigits*の引数**SQLBindParameter**このデータ型は無視されます。  
  
 10 進数字に対して返される値は、任意の 1 つの記述子フィールドの値に対応していません。 値は、次の表に示すように、SQL_DESC_SCALE] または [データの種類に応じて、SQL_DESC_PRECISION フィールドから取得できます。  
  
|SQL 型|対応する記述子フィールド<br /><br /> 小数点以下桁数|  
|--------------|----------------------------------------------------------|  
|すべての文字とバイナリ型|n/a|  
|すべての正確な数値型|SCALE|  
|SQL_BIT|n/a|  
|すべての概数型|n/a|  
|すべての datetime 型|PRECISION|  
|秒の部分ですべての間隔の種類|PRECISION|  
|すべての間隔型 (秒) コンポーネントがありません。|n/a|
