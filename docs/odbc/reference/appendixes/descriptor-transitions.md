---
title: 記述子の遷移 |マイクロソフトドキュメント
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307043"
---
# <a name="descriptor-transitions"></a>記述子の遷移
ODBC 記述子には、次の 3 つの状態があります。  
  
|State|説明|  
|-----------|-----------------|  
|D0|未割り当て記述子|  
|D1i|暗黙的に割り振られている記述子|  
|D1e|明示的に割り当てられた記述子|  
  
 次の表は、各 ODBC 関数が記述子の状態にどのように影響するかを示しています。  
  
## <a name="sqlallochandle"></a>ハンドル  
  
|D0<br /><br /> 未割り当て|D1i<br /><br /> Implicit|D1e<br /><br /> 明示|  
|------------------------|----------------------|----------------------|  
|D1i[1]|--|--|  
|D1e[2]|--|--|  
  
 [1] この行は *、HandleType*がSQL_HANDLE_STMTされたときの遷移を示しています。  
  
 [2] この行は *、HandleType*がSQL_HANDLE_DESCされたときの遷移を示しています。  
  
## <a name="sqlcopydesc"></a>を使用する  
  
|D0<br /><br /> 未割り当て|D1i<br /><br /> Implicit|D1e<br /><br /> 明示|  
|------------------------|----------------------|----------------------|  
|(IH)|--|--|  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
  
|D0<br /><br /> 未割り当て|D1i<br /><br /> Implicit|D1e<br /><br /> 明示|  
|------------------------|----------------------|----------------------|  
|--[1]|D0|--|  
|(IH)[2]|(HY017)|D0|  
  
 [1] この行は *、HandleType*がSQL_HANDLE_STMTされたときの遷移を示しています。  
  
 [2] この行は *、HandleType*がSQL_HANDLE_DESCされたときの遷移を示しています。  
  
## <a name="sqlgetdescfield-and-sqlgetdescrec"></a>フィールドと SQLGetDescRec  
  
|D0<br /><br /> 未割り当て|D1i<br /><br /> Implicit|D1e<br /><br /> 明示|  
|------------------------|----------------------|----------------------|  
|(IH)|--|--|  
  
## <a name="sqlsetdescfield-and-sqlsetdescrec"></a>SQL セットデズフィールドと SQL セットデセクレック  
  
|D0<br /><br /> 未割り当て|D1i<br /><br /> Implicit|D1e<br /><br /> 明示|  
|------------------------|----------------------|----------------------|  
|(IH)[1]|--|--|  
  
 [1] この行は、*記述子ハンドル*が ARD、APD、または IPD のハンドルであった場合の遷移、または*記述子ハンドル*が IRD のハンドルであり、*フィールド識別子*がSQL_DESC_ARRAY_STATUS_PTRまたはSQL_DESC_ROWS_PROCESSED_PTRされた場合 **(SQLSetDesc フィールド**の場合) を示しています。  
  
## <a name="all-other-odbc-functions"></a>その他すべての ODBC 関数  
  
|D0<br /><br /> 未割り当て|D1i<br /><br /> Implicit|D1e<br /><br /> 明示|  
|------------------------|----------------------|----------------------|  
|--|--|--|
