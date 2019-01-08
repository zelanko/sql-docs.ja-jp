---
title: SQLColAttributes のマッピング |Microsoft Docs
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
manager: craigg
ms.openlocfilehash: a7a1508d10431ba9975c44a2002faa4e5b913312
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2018
ms.locfileid: "53205341"
---
# <a name="sqlcolattributes-mapping"></a>SQLColAttributes のマッピング
アプリケーションを呼び出すと**SQLColAttributes**を通じて、ODBC 3 *.x*ドライバーでは、呼び出し**SQLColAttributes**にマップされて**SQLColAttribute**次のようにします。  
  
> [!NOTE]
>  使用されるプレフィックス*FieldIdentifier* ODBC 3 値 *.x*で使用される ODBC 2 から変更されました *。x*します。 新しいプレフィックスが"SQL_DESC";古いプレフィックス"SQL_COLUMN"が発生しました。  
  
1.  アプリケーションが ODBC 2 の場合は。*x*アプリケーション、 *fDescType* SQL_COLUMN_TYPE は、返された型は、簡潔な DATETIME 型、戻り値は、日付、時刻、およびタイムスタンプのコードのドライバー マネージャー マップします。  
  
2.  場合*fDescType* SQL_COLUMN_NAME、SQL_COLUMN_NULLABLE、または SQL_COLUMN_COUNT、ドライバー マネージャー呼び出し**SQLColAttribute**ドライバーで、 *FieldIdentifier*引数として適切な SQL_DESC_NAME、SQL_DESC_NULLABLE、SQL_DESC_COUNT にマップ*します。* その他のすべての値の*fDescType*ドライバーに渡されます。  
  
 ODBC 3 *.x*ドライバーは ODBC の 3 つすべてをサポートする必要があります *.x* *FieldIdentifiers*の**SQLColAttribute**します。  
  
 ODBC 3 *.x* SQL_COLUMN_PRECISION と SQL_DESC_PRECISION、SQL_COLUMN_SCALE と SQL_DESC_SCALE、および SQL_COLUMN_LENGTH および SQL_DESC_LENGTH ドライバーをサポートする必要があります。 有効桁数、小数点、および長さは、ODBC 3 で異なる方法で定義されるため、これらの値が異なる *.x*よりも ODBC 2 *。x*します。 詳細については、次を参照してください[列のサイズ、10 進数字、転送オクテット長、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)付録 d:。データ型。
