---
title: SQLSetScrollOptions 関数 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetScrollOptions
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetScrollOptions
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC]
ms.assetid: 2a825ba7-7942-4c23-bcdb-c80dc12f8c86
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dbdd2038bc217a7ca2a2efe08940c03c5da5d8f0
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2018
ms.locfileid: "53206751"
---
# <a name="sqlsetscrolloptions-function"></a>SQLSetScrollOptions 関数
**準拠**  
 バージョンが導入されました。ODBC 1.0 規格に準拠します。非推奨  
  
 **まとめ**  
 ODBC 3 *.x*、ODBC 2.0 関数**SQLSetScrollOptions**への呼び出しによって置き換えられました**SQLGetInfo**と**SQLSetStmtAttr**します。  
  
> [!NOTE]
>  どのようなドライバー マネージャーは、ときに、マッピングするには、この関数、ODBC 2 の詳細については *.x*アプリケーションの操作は、ODBC 3 *.x*ドライバーを参照してください[非推奨の関数のマッピング](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)付録 g:旧バージョンとの互換性のためのガイドラインをドライバーです。  
> 
> [!NOTE]
>  ドライバー マネージャーがマップされます**SQLSetScrollOptions** 、ODBC 3 の操作、アプリケーションの *.x*がサポートされていないドライバー **SQLSetScrollOptions**、ドライバーマネージャーに SQL_ROWSET_SIZE ステートメントのオプション、not、SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性を設定、*複合カーソル*引数**SQLSetScrollOption**します。 その結果、 **SQLSetScrollOptions**への呼び出しで複数の行をフェッチするときに、アプリケーションでは使用できません**SQLFetch**または**SQLFetchScroll**します。 フェッチの複数の行への呼び出しで場合にのみ使用できます**SQLExtendedFetch**します。  
  
## <a name="remarks"></a>コメント  
 アプリケーションは、64 ビットのオペレーティング システムで実行される場合は、[ODBC 64 ビットの情報](../../../odbc/reference/odbc-64-bit-information.md)を参照してください。  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
