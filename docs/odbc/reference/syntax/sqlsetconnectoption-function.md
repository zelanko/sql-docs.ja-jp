---
title: 関数を接続する |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 263b15cb75fb5c0c7c1d7aa630a8da171b9765a7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301597"
---
# <a name="sqlsetconnectoption-function"></a>SQLSetConnectOption 関数
**適合 性**  
 バージョン導入: ODBC 1.0 標準準拠: 非推奨  
  
 **まとめ**  
 ODBC 3 *.x*では、ODBC 2.0 関数**SQLSetConnect オプション**が**SQLSetConnectAttr**に置き換えられました。 詳細については、「[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)」を参照してください。  
  
> [!NOTE]
>  ODBC 2 *.x*アプリケーションが ODBC 3 *.x*ドライバーを使用して動作している場合にドライバー マネージャーがこの関数をマップする方法の詳細については、「[非推奨関数のマッピング](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)」を参照してください。  
  
## <a name="remarks"></a>解説  
 アプリケーションが 64 ビット オペレーティング システムで実行される場合は[、「ODBC 64](../../../odbc/reference/odbc-64-bit-information.md)ビット情報」を参照してください。  
  
> [!NOTE]  
>  ODBC 3.8 で導入された属性SQL_ASYNC_DBC_FUNCTION_ENABLEは **、SQLSetConnect オプション**ではサポートされていません。 接続ハンドルで非同期操作を使用するアプリケーションは **、 SQLSetConnectAttr**を使用する必要があります。  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
