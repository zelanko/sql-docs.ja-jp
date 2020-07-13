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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b3b559499273e885e23da10d9093a0ce9ff92393
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306623"
---
# <a name="c-to-sql-guid"></a>C から SQL へ: GUID
GUID ODBC C データ型の識別子は次のとおりです。  
  
 SQL_C_GUID  
  
 次の表は、GUID C データの変換先となる ODBC SQL データ型を示しています。 テーブル内の列と用語の詳細については、「[データを C から SQL データ型に変換する](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)」を参照してください。  
  
|SQL 型識別子|テスト|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR|列のバイト長 >= 36|該当なし|  
|SQL_VARCHAR|列のバイト長 < 36|22001|  
|SQL_LONGVARCHAR|データ値が有効な GUID ではありません|22018|  
|SQL_WCHAR|列の文字の長さ >= 36|該当なし|  
|SQL_WVARCHAR|列の文字の長さ < 36|22001|  
|SQL_WLONGVARCHAR|データ値が有効な GUID ではありません|22018|  
|SQL_GUID|なし [a]|該当なし|  
  
 [a] すべての16進値は、GUID として有効です。  
  
 ドライバーは、GUID C データ型からデータを変換するときの長さとインジケーターの値を無視し、データバッファーのサイズが GUID C データ型のサイズであると想定しています。 長さ/インジケーターの値は、 **Sqlputdata**の*StrLen_or_Ind*引数と、 **SQLBindParameter**の*StrLen_or_IndPtr*引数で指定されたバッファーに渡されます。 データバッファーは、 **Sqlputdata**の*DataPtr*引数と**SQLBindParameter**の*parametervalueptr*引数を使用して指定します。
