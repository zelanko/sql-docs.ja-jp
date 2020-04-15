---
title: SQL の属性のマッピング |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5c2c8386d6771141eaa0145a5d5964d70d6084d2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305418"
---
# <a name="sqlcolattributes-mapping"></a>SQLColAttributes のマッピング
アプリケーションが ODBC *3.x*ドライバーを使用して**SQLColAttributes**を呼び出すと、次のように**SQLCol 属性**への呼び出しが**マップ**されます。  
  
> [!NOTE]
>  ODBC *3.x*の*フィールド識別子*の値で使用されるプレフィックスは、ODBC *2.x*で使用されていたものから変更されました。 新しいプレフィックスは "SQL_DESC" です。古いプレフィックスは "SQL_COLUMN" でした。  
  
1.  アプリケーションが ODBC *2.x*アプリケーションで *、fDescType*がSQL_COLUMN_TYPEされ、返される型が簡潔な DATETIME 型の場合、ドライバー マネージャーは、日付、時刻、およびタイムスタンプのコードの戻り値をマップします。  
  
2.  *fDescType*がSQL_COLUMN_NAME、SQL_COLUMN_NULLABLE、またはSQL_COLUMN_COUNT場合、ドライバー マネージャーは、必要に応じて、SQL_DESC_NAME、SQL_DESC_NULLABLE、またはSQL_DESC_COUNTにマップされた*引数を*持つドライバーで**SQLColAttribute**を呼び出*します。* *fDescType*の他のすべての値は、ドライバーに渡されます。  
  
 ODBC *3.x*ドライバは **、SQLCol 属性**に一覧表示されているすべての ODBC *3.x* *フィールド識別子を*サポートしている必要があります。  
  
 ODBC *3.x*ドライバは、SQL_COLUMN_PRECISIONとSQL_DESC_PRECISION、SQL_COLUMN_SCALEとSQL_DESC_SCALE、SQL_COLUMN_LENGTHとSQL_DESC_LENGTHをサポートしている必要があります。 精度、小数点以下桁数、および長さは ODBC *2.x*とは異なる ODBC *3.x*で定義されているため、これらの値は異なります。 詳細については、「付録 D: データ型」の[「列サイズ、10 進数、転送オクテット長さ」および「表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)」を参照してください。
