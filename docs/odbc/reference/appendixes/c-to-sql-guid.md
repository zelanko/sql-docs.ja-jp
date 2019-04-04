---
title: 'C から SQL へ: GUID |Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from c to SQL types [ODBC], guid
- data conversions from C to SQL types [ODBC], guid
- GUID data type [ODBC]
ms.assetid: 9168b0b6-a828-4fef-b8cd-bdf439776f23
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: af0ed8307652ccf45e7fbfffb6c00355c8a8b004
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47745800"
---
# <a name="c-to-sql-guid"></a>C から SQL へ: GUID
GUID の ODBC C データ型の識別子です。  
  
 SQL_C_GUID  
  
 次の表は、ODBC SQL データ型の GUID の C データを変換する可能性がありますを示します。 列とテーブルの用語の詳細については、[C から SQL データ型への変換データ](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)を参照してください。  
  
|SQL 型識別子|テスト|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR|バイト長の列 > 36 を =|n/a|  
|SQL_VARCHAR|列のバイトの長さ < 36|22001|  
|SQL_LONGVARCHAR|データ値が有効な GUID ではありません。|22018|  
|SQL_WCHAR|文字の長さの列 > 36 を =|n/a|  
|SQL_WVARCHAR|列の長さ < 36 文字します。|22001|  
|SQL_WLONGVARCHAR|データ値が有効な GUID ではありません。|22018|  
|SQL_GUID|[A] [なし]|n/a|  
  
 [a] すべての 16 進数の値を GUID として有効です。  
  
 ドライバーでは、GUID の C データ型からデータを変換するとき長さ/インジケーター値を無視し、データ バッファーのサイズが GUID の C データ型のサイズであると仮定します。 長さまたはインジケーターの値が渡さ、 *StrLen_or_Ind*引数**SQLPutData**とで指定したバッファー、 *StrLen_or_IndPtr* 引数**SQLBindParameter**します。 データ バッファーを指定した、 *DataPtr*引数**SQLPutData**と*ParameterValuePtr*引数**SQLBindParameter**.
