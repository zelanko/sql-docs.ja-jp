---
title: SQLSetScrollOptions 関数 |Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81287270"
---
# <a name="sqlsetscrolloptions-function"></a>SQLSetScrollOptions 関数
**互換性**  
 導入されたバージョン: ODBC 1.0 標準準拠: 非推奨  
  
 **まとめ**  
 ODBC 3.x では、ODBC 2.0 関数**SQLSetScrollOptions**は**SQLGetInfo**と**SQLSetStmtAttr**の呼び出しに置き換えられてい*ます。*  
  
> [!NOTE]
>  *Odbc 2.x アプリケーションが*odbc *2.x ドライバーで*動作しているときに、ドライバーマネージャーがこの機能をマップする方法の詳細については、「付録 G: 旧バージョンとの互換性のためのドライバーガイドライン」の「[非推奨の関数のマッピング](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)」を参照してください。  
> 
> [!NOTE]
>  ドライバーマネージャーが、 **SQLSetScrollOptions**をサポートしていない ODBC 3.x ドライバーを使用しているアプリケーションの**SQLSetScrollOptions**をマップする場合、ドライバーマネージャーは、 **SQLSetScrollOption**の*RowsetSize*引数に、ステートメントの SQL_ATTR_ROW_ARRAY_SIZE の属性ではなく SQL_ROWSET_SIZE ステートメントオプションを設定*します。* 結果として、 **Sqlfetch**または**sqlfetchscroll**の呼び出しによって複数の行をフェッチするときに、アプリケーションで**SQLSetScrollOptions**を使用することはできません。 **SQLExtendedFetch**の呼び出しによって複数の行をフェッチする場合にのみ使用できます。  
  
## <a name="remarks"></a>Remarks  
 アプリケーションが64ビットオペレーティングシステムで実行される場合は、「 [ODBC 64 ビット情報](../../../odbc/reference/odbc-64-bit-information.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
