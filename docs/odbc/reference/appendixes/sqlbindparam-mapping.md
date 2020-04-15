---
title: マッピング |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLBindparam function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLBindParam
ms.assetid: 375f8f24-36de-4946-916e-c75abc6f070d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c1df595722297c91dc75398470912188e109e278
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305442"
---
# <a name="sqlbindparam-mapping"></a>SQLBindParam のマッピング
**SQLBindParam**は、ODBC では存在しないため、実際に非推奨と呼び出すことはできません。ただし、それはまだ重複した機能を表しています - ドライバー マネージャーは、ISO と Open Group 準拠のアプリケーションが使用するため、それをエクスポートする必要があります。 **SQLBindParameter には** **SQLBindParam**のすべての機能が含まれているため **、SQLBindParam**は**SQLBindParameter**の上にマップされます (基になるドライバーが ODBC *3.x*ドライバーの場合)。 ODBC *3.x*ドライバは **、SQLBindParam**を実装する必要はありません。  
  
## <a name="remarks"></a>解説  
 次の呼び出しが行われると、次**のことが**行われます。  
  
```  
SQLBindParam(   StatementHandle,    ParameterNumber,    ValueType,    ParameterType,    ColumnSize,    DecimalDigits,    ParameterValuePtr,    StrLen_or_IndPtr)  
```  
  
 ドライバー マネージャーは、次のようにドライバーで**SQLBind パラメーター**を呼び出します。  
  
```  
SQLBindParameter(   StatementHandle,    ParameterNumber,    SQL_PARAM_INPUT,    ValueType,    ParameterType,    ColumnSize,    DecimalDigits,    ParameterValuePtr,    BufferLength,    StrLen_or_IndPtr)  
```  
  
 アプリケーションが 64 ビット オペレーティング システムで実行される場合は[、「ODBC 64](../../../odbc/reference/odbc-64-bit-information.md)ビット情報」を参照してください。  
  
## <a name="see-also"></a>参照  
 [非推奨の関数のマッピング](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)
