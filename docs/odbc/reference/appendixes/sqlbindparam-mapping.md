---
title: SQLBindParam Mapping |Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305442"
---
# <a name="sqlbindparam-mapping"></a>SQLBindParam のマッピング
**SQLBindParam**は ODBC に存在しないため、実際には非推奨として呼び出すことはできません。ただし、これは重複した機能を表しています。 ISO とオープングループに準拠しているアプリケーションで使用されるため、ドライバーマネージャーはこれをエクスポートする必要があります。 **SQLBindParameter**には**SQLBindParam**のすべての機能が含まれているため、 **SQLBindParam**は**SQLBindParameter**の上にマップされます (基になるドライバー*が ODBC 3.x*ドライバーの場合)。 ODBC 3.x*ドライバーで*は、 **SQLBindParam**を実装する必要はありません。  
  
## <a name="remarks"></a>Remarks  
 **SQLBindParam**を呼び出すと、次のようになります。  
  
```  
SQLBindParam(   StatementHandle,    ParameterNumber,    ValueType,    ParameterType,    ColumnSize,    DecimalDigits,    ParameterValuePtr,    StrLen_or_IndPtr)  
```  
  
 ドライバーマネージャーは、次のようにドライバーで**SQLBindParameter**を呼び出します。  
  
```  
SQLBindParameter(   StatementHandle,    ParameterNumber,    SQL_PARAM_INPUT,    ValueType,    ParameterType,    ColumnSize,    DecimalDigits,    ParameterValuePtr,    BufferLength,    StrLen_or_IndPtr)  
```  
  
 アプリケーションが64ビットのオペレーティングシステムで実行される場合は、「 [ODBC 64 ビット情報](../../../odbc/reference/odbc-64-bit-information.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [非推奨の関数のマッピング](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)
