---
title: 記述子の遷移 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- state transitions [ODBC], descriptor
- transitioning states [ODBC], descriptor
- descriptor transitions [ODBC]
ms.assetid: 0cf24fe6-5e3c-45fa-81b8-4f52ddf8501d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ec5c26bdde8a0d470f2d93e753504bf1c51edcc0
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307043"
---
# <a name="descriptor-transitions"></a>記述子の遷移
ODBC 記述子には、次の3つの状態があります。  
  
|State|説明|  
|-----------|-----------------|  
|D0|未割り当ての記述子|  
|D1i|暗黙的に割り当てられた記述子|  
|D1e|明示的に割り当てられた記述子|  
  
 次の表は、各 ODBC 関数が記述子の状態にどのように影響するかを示しています。  
  
## <a name="sqlallochandle"></a>SQLAllocHandle  
  
|D0<br /><br /> 未割り当て|D1i<br /><br /> Implicit|D1e<br /><br /> 明示|  
|------------------------|----------------------|----------------------|  
|D1i [1]|--|--|  
|D1e [2]|--|--|  
  
 [1] この行は、 *Handletype*が SQL_HANDLE_STMT されたときの遷移を示しています。  
  
 [2] この行は、 *Handletype*が SQL_HANDLE_DESC されたときの遷移を示しています。  
  
## <a name="sqlcopydesc"></a>SQLCopyDesc  
  
|D0<br /><br /> 未割り当て|D1i<br /><br /> Implicit|D1e<br /><br /> 明示|  
|------------------------|----------------------|----------------------|  
|(IH)|--|--|  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
  
|D0<br /><br /> 未割り当て|D1i<br /><br /> Implicit|D1e<br /><br /> 明示|  
|------------------------|----------------------|----------------------|  
|--[1]|D0|--|  
|(IH)3|(HY017)|D0|  
  
 [1] この行は、 *Handletype*が SQL_HANDLE_STMT されたときの遷移を示しています。  
  
 [2] この行は、 *Handletype*が SQL_HANDLE_DESC されたときの遷移を示しています。  
  
## <a name="sqlgetdescfield-and-sqlgetdescrec"></a>SQLGetDescField と SQLGetDescRec  
  
|D0<br /><br /> 未割り当て|D1i<br /><br /> Implicit|D1e<br /><br /> 明示|  
|------------------------|----------------------|----------------------|  
|(IH)|--|--|  
  
## <a name="sqlsetdescfield-and-sqlsetdescrec"></a>SQLSetDescField と SQLSetDescRec  
  
|D0<br /><br /> 未割り当て|D1i<br /><br /> Implicit|D1e<br /><br /> 明示|  
|------------------------|----------------------|----------------------|  
|(IH)1|--|--|  
  
 [1] この行は、*記述子ハンドル*が、APD、または IPD のハンドルである**ときの遷移**を示します。または、*記述子ハンドル*が IRD および*FieldIdentifier* SQL_DESC_ARRAY_STATUS_PTR was のハンドルである場合は、または SQL_DESC_ROWS_PROCESSED_PTR ます。  
  
## <a name="all-other-odbc-functions"></a>その他すべての ODBC 関数  
  
|D0<br /><br /> 未割り当て|D1i<br /><br /> Implicit|D1e<br /><br /> 明示|  
|------------------------|----------------------|----------------------|  
|--|--|--|
