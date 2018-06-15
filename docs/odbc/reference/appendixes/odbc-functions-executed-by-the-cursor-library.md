---
title: カーソル ライブラリによって実行された ODBC 関数 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- cursor library [ODBC], functions
- functions [ODBC], cursor library
- ODBC functions [ODBC], cursor library
- ODBC cursor library [ODBC], functions
ms.assetid: 2f1d3386-7e59-4d55-a5b4-3440b61343a3
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 51e123ef04153579227f92e449c3dc4e46f6ac0d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32907757"
---
# <a name="odbc-functions-executed-by-the-cursor-library"></a>カーソル ライブラリによって実行された ODBC 関数
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないように、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 カーソル ライブラリは、次の関数を実行します。 アプリケーションがこの一覧に関数を呼び出すときに、ドライバー マネージャーは、ドライバーではなく、カーソル ライブラリを呼び出します。 関数を実行するときに、カーソル ライブラリにドライバーを呼び出すことがありますに注意してください。  
  
|||  
|-|-|  
|**SQLBindCol**|**SQLGetStmtOption**|  
|**SQLBindParam**|**SQLNativeSql**|  
|**SQLBindParameter**|**SQLNumParams**|  
|**SQLCloseCursor**|**SQLParamOptions**|  
|**SQLEndTran**|**SQLRowCount**|  
|**SQLExtendedFetch**|**SQLSetConnectAttr**|  
|**SQLFetchScroll**|**SQLSetConnectOption**|  
|**SQLFreeHandle**|**Sqlsetdescfield による**|  
|**SQLFreeStmt**|**Sqlsetdescrec による**|  
|**SQLGetData**|**SQLSetPos**|  
|**SQLGetDescField**|**SQLSetScrollOptions**|  
|**Sqlgetdescrec による**|**SQLSetStmtAttr**|  
|**SQLGetFunctions**|**SQLSetStmtOption**|  
|**SQLGetInfo**|**SQLTransact**|  
|**SQLGetStmtAttr**||
