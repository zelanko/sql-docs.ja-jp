---
title: SQLSetConnectOption 関数 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetConnectOption
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetConnectOption
helpviewer_keywords:
- SQLSetConnectOption function [ODBC]
ms.assetid: 8cd2c2a2-25c8-4aff-951c-b593bbfc90ad
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f2a4965fedc7da47751742e863119b818a9fcba9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47646360"
---
# <a name="sqlsetconnectoption-function"></a>SQLSetConnectOption 関数
**準拠**  
 バージョンで導入されました ODBC 1.0 標準準拠: 非推奨とされます。  
  
 **概要**  
 ODBC 3 *.x*、ODBC 2.0 関数**SQLSetConnectOption**置き換わりました**SQLSetConnectAttr**します。 詳細については、「[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)」を参照してください。  
  
> [!NOTE]  
>  どのようなドライバー マネージャーは、ときに、マッピングするには、この関数、ODBC 2 の詳細については *.x*アプリケーションの操作は、ODBC 3 *.x*ドライバーを参照してください[非推奨の関数のマッピング](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)".  
  
## <a name="remarks"></a>コメント  
 参照してください[ODBC 64 ビットの情報](../../../odbc/reference/odbc-64-bit-information.md)場合、アプリケーションが 64 ビットのオペレーティング システムで実行します。  
  
> [!NOTE]  
>  ODBC 3.8 に導入された SQL_ASYNC_DBC_FUNCTION_ENABLE 属性でサポートされていない**SQLSetConnectOption**します。 接続ハンドルに対して非同期操作を使用するアプリケーションを使用する必要があります**SQLSetConnectAttr**します。  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
