---
title: SQLColAttributes マッピング |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLColAttributes
- SQLColAttribute function [ODBC], mapping
ms.assetid: 30e25719-176b-4c48-97d4-920766b22412
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 615ee316c8fe515ebbd3d983cd32e70bbcb8681e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqlcolattributes-mapping"></a>SQLColAttributes マッピング
アプリケーションを呼び出すと**SQLColAttributes**から ODBC 3 *.x*ドライバーへの呼び出し**SQLColAttributes**にマップされて**SQLColAttribute**次のようにします。  
  
> [!NOTE]  
>  使用されるプレフィックス*FieldIdentifier* ODBC 3 値 *.x*で使用される ODBC 2 から変更されました*。x*です。 新しいプレフィックスは"SQL_DESC"です。古いプレフィックスは、"SQL_COLUMN"でした。  
  
1.  アプリケーションが ODBC 2 の場合は。*x*アプリケーション、 *fDescType* SQL_COLUMN_TYPE は、返された型は、簡潔な DATETIME 型では、戻り値は、日付、時刻、およびタイムスタンプのコードについては、ドライバー マネージャーのマップ。  
  
2.  場合*fDescType* SQL_COLUMN_NAME、SQL_COLUMN_NULLABLE、または SQL_COLUMN_COUNT、ドライバー マネージャーの呼び出しは、 **SQLColAttribute**ドライバーで、 *FieldIdentifier*SQL_DESC_NAME、またはにマップ SQL_DESC_NULLABLE、SQL_DESC_COUNT、必要に応じて引数*です。* 他のすべての値*fDescType*ドライバーに渡されます。  
  
 ODBC 3 *.x*ドライバーは、すべての ODBC 3 をサポートする必要があります *.x* *FieldIdentifiers*に登録されている**SQLColAttribute**です。  
  
 ODBC 3 *.x*ドライバー必要があります SQL_COLUMN_PRECISION と SQL_DESC_PRECISION、SQL_COLUMN_SCALE と SQL_DESC_SCALE、および SQL_COLUMN_LENGTH およびサポート SQL_DESC_LENGTH です。 ODBC 3 に有効桁数、小数点以下桁数、および長さが異なる方法でに定義されるため、これらの値が異なる *.x* ODBC 2 よりも*。x*です。 詳細については、次を参照してください。[列のサイズ、小数点以下桁数、転送オクテット長さ、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)付録 d: データ型にします。
