---
title: SQLColAttributes マッピング |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLColAttributes
- SQLColAttribute function [ODBC], mapping
ms.assetid: 30e25719-176b-4c48-97d4-920766b22412
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 08abd0128a6fa2a478af0e9dc9c292ff973ace79
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68064487"
---
# <a name="sqlcolattributes-mapping"></a>SQLColAttributes のマッピング
アプリケーションが ODBC *3. x*ドライバーを使用して**sqlcolattributes**を呼び出すと、 **sqlcolattributes**への呼び出しは次のように**sqlcolattributes**にマップされます。  
  
> [!NOTE]
>  *Odbc 3.x*の*FieldIdentifier*値で使用されるプレフィックスが、odbc 2.x で使用されるものから変更さ*れました*。 新しいプレフィックスは "SQL_DESC" です。古いプレフィックスは "SQL_COLUMN" でした。  
  
1.  アプリケーション*が ODBC 2.x*アプリケーションであり、 *fDescType*が SQL_COLUMN_TYPE で、戻り値の型が簡潔な DATETIME 型の場合、ドライバーマネージャーは日付、時刻、およびタイムスタンプのコードの戻り値をマップします。  
  
2.  *FDescType*が SQL_COLUMN_NAME、SQL_COLUMN_NULLABLE、または SQL_COLUMN_COUNT の場合、ドライバーマネージャーは、必要に応じて、SQL_DESC_NAME、SQL_DESC_NULLABLE、または SQL_DESC_COUNT にマップされた*FieldIdentifier*引数を使用して、ドライバーの**sqlcolattribute**を呼び出し*ます。* *FDescType*のその他のすべての値は、ドライバーに渡されます。  
  
 ODBC 3.x*ドライバーは*、 **sqlcolattribute**に対してリストされているすべて*の odbc 3.x* *FieldIdentifiers*をサポートしている必要があります。  
  
 ODBC 3.x ドライバーは、SQL_COLUMN_PRECISION と SQL_DESC_PRECISION、SQL_COLUMN_SCALE と SQL_DESC_SCALE、および SQL_COLUMN_LENGTH と SQL_DESC_LENGTH をサポートしている必要が*あります。* *Odbc 2.x*では、有効桁数、小数点以下桁数、および長さが異なるため、これらの値は異なり*ます。* 詳細については、「付録 D: データ型」の「[列のサイズ、10進数、転送オクテットの長さ、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)」を参照してください。
