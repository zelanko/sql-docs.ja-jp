---
title: 重複する特徴 |Microsoft Docs
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
ms.openlocfilehash: ca73b5b9b41c99bd6db8e6181fa3582cae47c1d1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68046903"
---
# <a name="duplicated-features"></a>重複する機能
Odbc 3.x 関数によって、次*の odbc 2.x*関数** が複製されました。 その結果 *、odbc 2.x 関数は*odbc 3.x では非推奨とされ*ます。* ODBC *3. x*関数は、置換関数と呼ばれます。  
  
 アプリケーションが非推奨の ODBC 2.x*関数を*使用し、基になるドライバー*が odbc 3.x*ドライバーである場合、ドライバーマネージャーは関数呼び出しを対応する置換関数にマップします。 この規則の唯一の例外は**SQLExtendedFetch**です。 (次の表の最後にある脚注を参照してください)。これらのマッピングの詳細については、「付録 G: 旧バージョンとの互換性のためのドライバーガイドライン」の「[非推奨の関数のマッピング](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)」を参照してください。  
  
 アプリケーションが置換関数を使用し、基になるドライバー*が ODBC 2.x*ドライバーである場合、ドライバーマネージャーは関数呼び出しを対応する非推奨の関数にマップします。  
  
|ODBC *2.x*関数|ODBC *3.x*関数|  
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
  
 [1] 関数**SQLExtendedFetch**は重複しています。**Sqlfetchscroll**は ODBC 3.x と同じ機能を提供*します。* ただし *、ODBC 3.x*ドライバーに対して実行する場合、ドライバーマネージャーは**SQLExtendedFetch**を**sqlfetchscroll**にマップしません。 詳細については、「付録 G: ドライバー[マネージャー](../../../odbc/reference/appendixes/what-the-driver-manager-does.md)による旧バージョンとの互換性のためのドライバーガイドライン」を参照してください。 ドライバーマネージャーは *、ODBC 2.x*ドライバーに対して実行するときに**Sqlfetchscroll**を**SQLExtendedFetch**にマップします。  
  
> [!NOTE]
>  関数**SQLBindParam**は特殊なケースです。 **SQLBindParam**の機能は重複しています。 これ*は ODBC 2.x*関数ではなく、Open GROUP と ISO 標準に存在する関数です。 この関数によって提供される機能は、 **SQLBindParameter**の機能によって完全に包括されています。 その結果、ドライバーマネージャーは、基になるドライバーが ODBC 3.x ドライバーである場合に、 **SQLBindParam**への呼び出しを**SQLBindParameter**にマップ*します。* ただし、基に*なるドライバーが ODBC 2.x*ドライバーの場合、ドライバーマネージャーはこのマッピングを実行しません。
