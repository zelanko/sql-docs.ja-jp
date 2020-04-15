---
title: 関数を指定する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetConnectOption
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetConnectOption
helpviewer_keywords:
- SQLGetConnectOption function [ODBC]
ms.assetid: 59cde899-7957-4b5e-8677-f34d3b859bfd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 94a29637365862990ea067f663023fae04a7af3e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285572"
---
# <a name="sqlgetconnectoption-function"></a>SQLGetConnectOption 関数
**適合 性**  
 バージョン導入: ODBC 1.0 標準準拠: 非推奨  
  
 **まとめ**  
 ODBC *3.x*では、ODBC *2.x*関数**SQLGetConnect オプション**が**SQLGetConnectAttr**に置き換えられました。 詳細については、「 [SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)」を参照してください。  
  
> [!NOTE]
>  ODBC *2.x*アプリケーションが ODBC *3.x*ドライバーを使用して動作しているときにドライバー マネージャーがこの関数をマップする方法の詳細については、「付録 G: 下位互換性のためのドライバーガイドライン」の[「非推奨関数のマッピング](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)」を参照してください。  
> 
> [!NOTE]
>  ODBC 3.8 で導入された属性SQL_ASYNC_DBC_FUNCTION_ENABLEは **、SQLGetConnect オプション**ではサポートされていません。 接続ハンドルで非同期操作を使用するアプリケーションは、 **SQLGetConnectAttr**を使用する必要があります。  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
