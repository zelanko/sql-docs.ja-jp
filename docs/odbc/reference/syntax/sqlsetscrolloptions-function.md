---
title: "SQLSetScrollOptions 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLSetScrollOptions
apilocation: sqlsrv32.dll
apitype: dllExport
f1_keywords: SQLSetScrollOptions
helpviewer_keywords: SQLSetScrollOptions function [ODBC]
ms.assetid: 2a825ba7-7942-4c23-bcdb-c80dc12f8c86
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8e8f0d027727a4bf6c64f9868913544c41661838
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="sqlsetscrolloptions-function"></a>SQLSetScrollOptions 関数
**準拠**  
 バージョンで導入された: ODBC 1.0 標準準拠: 非推奨  
  
 **概要**  
 ODBC 3*.x*、ODBC 2.0 関数**SQLSetScrollOptions**への呼び出しから置き換え**SQLGetInfo**と**SQLSetStmtAttr**です。  
  
> [!NOTE]  
>  詳細については、どのようなドライバー マネージャーは、この関数にする際にマップ ODBC 2*.x*アプリケーションは、ODBC 3 と連携して*.x*ドライバーを参照してください[非推奨機能のマッピング](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)旧バージョンとの互換性のための付録 g: ドライバーのガイドライン」にします。  
  
> [!NOTE]  
>  ドライバー マネージャーのマップと**SQLSetScrollOptions** ODBC 3 を使用するアプリケーションの*.x*ドライバーをサポートしない**SQLSetScrollOptions**、ドライバーマネージャーに SQL_ROWSET_SIZE ステートメントのオプション、not、SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性を設定、*複合カーソル*引数**SQLSetScrollOption**です。 その結果、 **SQLSetScrollOptions**への呼び出しによって複数の行をフェッチするときに、アプリケーションでは使用できません**SQLFetch**または**SQLFetchScroll**です。 フェッチの複数の行への呼び出しによって場合にのみ使用できます**SQLExtendedFetch**です。  
  
## <a name="remarks"></a>解説  
 アプリケーションは、64 ビット オペレーティング システムで実行される場合は、次を参照してください。 [ODBC 64 ビット情報](../../../odbc/reference/odbc-64-bit-information.md)です。  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
