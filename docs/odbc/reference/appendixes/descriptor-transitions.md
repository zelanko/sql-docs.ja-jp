---
title: "記述子遷移 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- state transitions [ODBC], descriptor
- transitioning states [ODBC], descriptor
- descriptor transitions [ODBC]
ms.assetid: 0cf24fe6-5e3c-45fa-81b8-4f52ddf8501d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 280d35d8ce03d3d7685441c12d99c05c9ff5f451
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="descriptor-transitions"></a>記述子の遷移
ODBC 記述子では、次の 3 つの状態があります。  
  
|状態|Description|  
|-----------|-----------------|  
|D0|未割り当ての記述子|  
|D1i|暗黙的に割り当てられた記述子|  
|D1e|明示的に割り当てられた記述子|  
  
 次の表では、各 ODBC 関数が、記述子の状態にどのように影響する方法を示しています。  
  
## <a name="sqlallochandle"></a>SQLAllocHandle  
  
|D0<br /><br /> 未割り当て|D1i<br /><br /> 暗黙の型|D1e<br /><br /> 明示|  
|------------------------|----------------------|----------------------|  
|D1i [1]|--|--|  
|D1e [2]|--|--|  
  
 [1] この行は、移行を示しています。 ときに*HandleType* SQL_HANDLE_STMT をがします。  
  
 [2] この行は、移行を示しています。 ときに*HandleType* SQL_HANDLE_DESC をがします。  
  
## <a name="sqlcopydesc"></a>SQLCopyDesc  
  
|D0<br /><br /> 未割り当て|D1i<br /><br /> 暗黙の型|D1e<br /><br /> 明示|  
|------------------------|----------------------|----------------------|  
|(組み込み)|--|--|  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
  
|D0<br /><br /> 未割り当て|D1i<br /><br /> 暗黙の型|D1e<br /><br /> 明示|  
|------------------------|----------------------|----------------------|  
|--[1]|D0|--|  
|(組み込み)[2]|(HY017)|D0|  
  
 [1] この行は、移行を示しています。 ときに*HandleType* SQL_HANDLE_STMT をがします。  
  
 [2] この行は、移行を示しています。 ときに*HandleType* SQL_HANDLE_DESC をがします。  
  
## <a name="sqlgetdescfield-and-sqlgetdescrec"></a>SQLGetDescField と SQLGetDescRec  
  
|D0<br /><br /> 未割り当て|D1i<br /><br /> 暗黙の型|D1e<br /><br /> 明示|  
|------------------------|----------------------|----------------------|  
|(組み込み)|--|--|  
  
## <a name="sqlsetdescfield-and-sqlsetdescrec"></a>Sqlsetdescfield によると SQLSetDescRec  
  
|D0<br /><br /> 未割り当て|D1i<br /><br /> 暗黙の型|D1e<br /><br /> 明示|  
|------------------------|----------------------|----------------------|  
|(組み込み)[1]|--|--|  
  
 [1] この行は、移行を示していますときに*DescriptorHandle* ARD、APD、または、IPD のハンドルがまたは (の**SQLSetDescField**) と*DescriptorHandle* 、IRD のハンドルをされました。および*FieldIdentifier* SQL_DESC_ARRAY_STATUS_PTR または SQL_DESC_ROWS_PROCESSED_PTR されました。  
  
## <a name="all-other-odbc-functions"></a>他のすべての ODBC 関数  
  
|D0<br /><br /> 未割り当て|D1i<br /><br /> 暗黙の型|D1e<br /><br /> 明示|  
|------------------------|----------------------|----------------------|  
|--|--|--|

