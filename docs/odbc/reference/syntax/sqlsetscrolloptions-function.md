---
title: 関数 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetScrollOptions
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLSetScrollOptions
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC]
ms.assetid: 2a825ba7-7942-4c23-bcdb-c80dc12f8c86
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 056fc203581e1d5d8323b09ac62d692093d8c0f5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287270"
---
# <a name="sqlsetscrolloptions-function"></a>SQLSetScrollOptions 関数
**適合 性**  
 バージョン導入: ODBC 1.0 標準準拠: 非推奨  
  
 **まとめ**  
 ODBC *3.x*では、ODBC 2.0 関数**SQLSetScrollOptions**が**呼**び**出しに**置き換えられました。  
  
> [!NOTE]
>  ODBC *2.x*アプリケーションが ODBC *3.x*ドライバーを使用して動作しているときにドライバー マネージャーがこの関数をマップする方法の詳細については、「付録 G: 下位互換性のためのドライバーガイドライン」の[「非推奨関数のマッピング](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)」を参照してください。  
> 
> [!NOTE]
>  ドライバー マネージャーは **、SQLSetScrollOptions**をサポートしていない ODBC *3.x*ドライバーを使用して作業するアプリケーションの**SQLSetScrollOptions**をマップすると、ドライバー マネージャーは、SQL_ATTR_ROW_ARRAY_SIZE ステートメント*RowsetSize*属性ではなく、SQL_ROWSET_SIZE ステートメント**オプションを設定**します。 その結果、SQLFetch または**SQLFetchScroll**の呼び出しによって複数の行をフェッチする場合、アプリケーションで**SQLSetScrollOptions** **を**使用することはできません。 **SQLExtendedFetch**の呼び出しによって複数の行をフェッチする場合にのみ使用できます。  
  
## <a name="remarks"></a>解説  
 アプリケーションが 64 ビット オペレーティング システムで実行される場合は[、「ODBC 64 ビット情報](../../../odbc/reference/odbc-64-bit-information.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
