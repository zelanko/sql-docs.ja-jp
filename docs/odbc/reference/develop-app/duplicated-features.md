---
title: 機能を重複しています |。Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- duplicated functions [ODBC]
- compatibility [ODBC], duplicated functions
- ODBC drivers [ODBC], backward compatibility
- functions [ODBC], duplicated functions
- backward compatibility [ODBC], duplicated functions
ms.assetid: 641b16bc-f791-46d8-b093-31736473fe3d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 84752b7e23c5394757764bf5ade57cb54004b01a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62943148"
---
# <a name="duplicated-features"></a>重複する機能
次の ODBC 2.*x*関数が ODBC 3 が重複しています *。x*関数。 その結果、ODBC 2。*x* ODBC 3 関数が非推奨とされます *。x*します。 ODBC 3。*x*関数を置換関数と呼びます。  
  
 アプリケーションが非推奨の ODBC 2 を使用する場合。*x*関数であり、基になるドライバーが、ODBC 3 *。x*ドライバー、ドライバー マネージャーが対応する置換関数の関数呼び出しをマップします。 このルールの唯一の例外は**SQLExtendedFetch**します。 (次の表の最後の脚注を参照してください)。これらのマッピングの詳細については、次を参照してください[非推奨の関数のマッピング](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)で付録 g:。旧バージョンとの互換性のためのガイドラインをドライバーです。  
  
 ODBC 2 は、アプリケーションが、置換する関数と基になるドライバーを使用する場合。*x*ドライバー、ドライバー マネージャーは、マップに対応する非推奨の関数の関数呼び出し。  
  
|ODBC 2。*x*関数|ODBC 3。*x*関数|  
|-------------------------|-------------------------|  
|**SQLAllocConnect**|**SQLAllocHandle**|  
|**SQLAllocEnv**|**SQLAllocHandle**|  
|**SQLAllocStmt**|**SQLAllocHandle**|  
|**SQLColAttributes**|**SQLColAttribute**|  
|**SQLError**|**SQLGetDiagRec**|  
|**SQLExtendedFetch**[1]|**SQLFetchScroll**|  
|**SQLFreeConnect**|**SQLFreeHandle**|  
|**SQLFreeEnv**|**SQLFreeHandle**|  
|**SQLGetConnectOption**|**SQLGetConnectAttr**|  
|**SQLGetStmtOption**|**SQLGetStmtAttr**|  
|**SQLParamOptions**|**SQLSetStmtAttr**、 **SQLGetStmtAttr**|  
|**SQLSetConnectOption**|**SQLSetConnectAttr**|  
|**SQLSetParam**|**SQLBindParameter**|  
|**SQLSetStmtOption**|**SQLSetStmtAttr**|  
|**SQLTransact**|**SQLEndTran**|  
  
 [1]、関数**SQLExtendedFetch**が重複している機能です。**SQLFetchScroll** ODBC 3 で同じ機能を提供します *。x*します。 ただし、ドライバー マネージャーがマップされない**SQLExtendedFetch**に**SQLFetchScroll**ときに、ODBC 3 に対して *。x*ドライバー。 詳細については、次を参照してください[、ドライバー マネージャーが何](../../../odbc/reference/appendixes/what-the-driver-manager-does.md)で付録 g:。旧バージョンとの互換性のためのガイドラインをドライバーです。 ドライバー マネージャー マップ**SQLFetchScroll**に**SQLExtendedFetch**ときに、ODBC 2 に対して *。x*ドライバー。  
  
> [!NOTE]
>  関数は、 **SQLBindParam**特殊なケースです。 **SQLBindParam**が重複している機能です。 これは、ODBC 2 ではありません *.x*関数が、Open Group および ISO 標準に存在する関数。 この関数によって提供される機能が完全に含まれているの**SQLBindParameter**します。 ドライバー マネージャーがへの呼び出しをマップするため、 **SQLBindParam**に**SQLBindParameter**基になるドライバーが、ODBC 3 の場合 *。x*ドライバー。 ただし、基になるドライバーが、ODBC 2 が場合 *.x*ドライバー、ドライバー マネージャーはこのマッピングを実行していません。
