---
title: 10 進数 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- size of data types [ODBC]
- decimal digits of data types [ODBC]
- data types [ODBC], decimal digits
- SQL data types [ODBC], column characteristics
ms.assetid: 07f3d1fc-b4ee-4693-b342-330b2231b6d0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4921a6162b6d711e657f223b5be5783dfa37bca8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285162"
---
# <a name="decimal-digits"></a>10 進数字
10 進および数値データ型の*10 進数の桁数*は、小数点の右側の最大桁数、つまりデータの位取りとして定義されます。 近似浮動小数点数の列またはパラメーターの場合、小数点の右側の桁数が固定されていないため、小数点以下桁数は未定義です。 秒コンポーネントを含む日時データまたは間隔データの場合、10 進数は、データの秒コンポーネントの小数点の右側の桁数として定義されます。  
  
 SQL_DECIMALデータ型とSQL_NUMERICデータ型の場合、最大スケールは通常、最大精度と同じです。 ただし、一部のデータ ソースでは、最大スケールに別の制限が課されます。 データ型に許容される最小および最大のスケールを決定するために、アプリケーションは**SQLGetTypeInfo**を呼び出します。  
  
 次の表に、簡潔な SQL データ型ごとに定義されている 10 進数の数字を示します。  
  
|SQL 型|数字|  
|--------------|--------------------|  
|すべての文字型とバイナリ型[a]|該当なし|  
|SQL_DECIMAL<br />SQL_NUMERIC|小数点の右側に定義された桁数。 たとえば、NUMERIC(10,3) として定義されている列の位取りは 3 です。 これは、指数表記を使用せずに非常に大きな数値の格納をサポートする負の数を指定できます。たとえば、"12000" はスケールが -3 の "12" として格納できます。|  
|SQL_DECIMALおよびSQL_NUMERIC以外のすべての正確な数値型|0|  
|すべての近似データ型[a]|該当なし|  
|SQL_TYPE_DATE、および秒コンポーネントのないすべての間隔タイプ[a]|該当なし|  
|SQL_TYPE_DATEを除くすべての日時型、および秒コンポーネントを持つすべての間隔タイプ|値の秒部分の小数点の右側の桁数 (秒の小数部)。 この数値は負の値にすることはできません。|  
|SQL_GUID|該当なし|  
  
 [a] このデータ型では **、SQLBindParameter**の*10 進数の*引数は無視されます。  
  
 10 進数の値が、1 つの記述子フィールドの値に対応していません。 値は、次の表に示すように、データ型に応じて、SQL_DESC_SCALEまたはSQL_DESC_PRECISION フィールドのいずれかから取得できます。  
  
|SQL 型|対応する記述子フィールド<br /><br /> 桁|  
|--------------|----------------------------------------------------------|  
|すべての文字とバイナリ型|該当なし|  
|すべての正確な数値型|SCALE|  
|SQL_BIT|該当なし|  
|すべての近似数値型|該当なし|  
|すべての日時型|PRECISION|  
|秒コンポーネントを持つすべての間隔タイプ|PRECISION|  
|秒コンポーネントのないすべての間隔タイプ|該当なし|
