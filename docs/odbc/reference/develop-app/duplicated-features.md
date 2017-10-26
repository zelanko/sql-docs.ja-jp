---
title: "機能を重複しています |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- duplicated functions [ODBC]
- compatibility [ODBC], duplicated functions
- ODBC drivers [ODBC], backward compatibility
- functions [ODBC], duplicated functions
- backward compatibility [ODBC], duplicated functions
ms.assetid: 641b16bc-f791-46d8-b093-31736473fe3d
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b12ba1b5b8c70e6ab0f7efe6f0811984411a6022
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="duplicated-features"></a>重複する機能
次の ODBC 2.*x* ODBC 3 で関数が重複しています*。x*関数。 結果として、ODBC 2 です。*x*関数、ODBC 3 で廃止されました*。x*です。 ODBC 3 です。*x*関数を置換機能と呼びます。  
  
 アプリケーションは、非推奨の ODBC 2 を使用する場合。*x*関数であり、基になるドライバーが ODBC 3* 。x*ドライバー、ドライバー マネージャーが対応する置換関数の関数呼び出しをマップします。 このルールの唯一の例外は**SQLExtendedFetch**です。 (脚注、次の表の最後を参照してください)。これらのマッピングの詳細については、次を参照してください。[非推奨機能のマッピング](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)旧バージョンとの互換性のための付録 g: ドライバーのガイドライン」にします。  
  
 ODBC 2 には、アプリケーションが、置換する関数と、基になるドライバーを使用している場合です。*x*ドライバー、ドライバー マネージャーが対応する非推奨の関数を関数呼び出しをマップします。  
  
|ODBC 2 です。*x*関数|ODBC 3 です。*x*関数|  
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
  
 [1]、関数**SQLExtendedFetch**が重複している機能です。**SQLFetchScroll** ODBC 3 で同様の機能を提供します*。x*です。 ただし、ドライバー マネージャーはマップされていない**SQLExtendedFetch**に**SQLFetchScroll**されるときに ODBC 3 に対して*。x*ドライバー。 詳細については、次を参照してください。 [、ドライバー マネージャーが何](../../../odbc/reference/appendixes/what-the-driver-manager-does.md)旧バージョンとの互換性のための付録 g: ドライバーのガイドライン」にします。 ドライバー マネージャーは、マップ**SQLFetchScroll**に**SQLExtendedFetch**されるときに ODBC 2 に対する*。x*ドライバー。  
  
> [!NOTE]  
>  関数は、 **SQLBindParam**特殊なケースです。 **SQLBindParam**が重複している機能です。 これは、ODBC 2 ではありません*.x*関数が、Open Group および ISO 規格に存在する関数。 この関数によって提供される機能はのによって完全に包含されています。 **SQLBindParameter**です。 ドライバー マネージャーがへの呼び出しをマップするため、 **SQLBindParam**に**SQLBindParameter**基になるドライバーが ODBC 3 の場合*。x*ドライバー。 ただし、ときに、基になるドライバーは、ODBC 2*.x*ドライバー、ドライバー マネージャーはこのマッピングを実行していません。

