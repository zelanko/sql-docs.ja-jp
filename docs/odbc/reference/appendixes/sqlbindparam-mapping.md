---
title: SQLBindParam のマッピング |Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 26f9bdc0564b98132bb5ec413c99917e78e4d62e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47855180"
---
# <a name="sqlbindparam-mapping"></a>SQLBindParam のマッピング
**SQLBindParam**呼び出すことができません本当に廃止されたため、そこにあったしない ODBC では、まだに重複している機能を表す、ただし、-、ドライバー マネージャーは、ISO と開いているグループに準拠したアプリケーションで使用されて、エクスポートする必要があります。 **SQLBindParameter**のすべての機能が含まれています**SQLBindParam**、 **SQLBindParam**の上にマップする**SQLBindParameter**(基になるドライバーがの場合、ODBC 3 *.x*ドライバー)。 ODBC 3 *.x*ドライバーが実装する必要はありません**SQLBindParam**します。  
  
## <a name="remarks"></a>コメント  
 ときに、次の呼び出し**SQLBindParam**されます。  
  
```  
SQLBindParam(   StatementHandle,    ParameterNumber,    ValueType,    ParameterType,    ColumnSize,    DecimalDigits,    ParameterValuePtr,    StrLen_or_IndPtr)  
```  
  
 ドライバー マネージャー呼び出し**SQLBindParameter**ドライバーとして次のとおりです。  
  
```  
SQLBindParameter(   StatementHandle,    ParameterNumber,    SQL_PARAM_INPUT,    ValueType,    ParameterType,    ColumnSize,    DecimalDigits,    ParameterValuePtr,    BufferLength,    StrLen_or_IndPtr)  
```  
  
 参照してください[ODBC 64 ビットの情報](../../../odbc/reference/odbc-64-bit-information.md)場合、アプリケーションが 64 ビットのオペレーティング システムで実行します。  
  
## <a name="see-also"></a>参照  
 [非推奨の関数のマッピング](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)
