---
title: "SQLSetConnectOption 関数 |Microsoft ドキュメント"
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
apiname: SQLSetConnectOption
apilocation: sqlsrv32.dll
apitype: dllExport
f1_keywords: SQLSetConnectOption
helpviewer_keywords: SQLSetConnectOption function [ODBC]
ms.assetid: 8cd2c2a2-25c8-4aff-951c-b593bbfc90ad
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b133c5a34dd37f02dd930d2a035c6b69ea49b093
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="sqlsetconnectoption-function"></a>SQLSetConnectOption 関数
**準拠**  
 バージョンで導入された: ODBC 1.0 標準準拠: 非推奨  
  
 **概要**  
 ODBC 3*.x*、ODBC 2.0 関数**SQLSetConnectOption**代わりました**SQLSetConnectAttr**です。 詳細については、次を参照してください。 [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)です。  
  
> [!NOTE]  
>  詳細については、どのようなドライバー マネージャーは、この関数にする際にマップ ODBC 2*.x*アプリケーションは、ODBC 3 と連携して*.x*ドライバーを参照してください[非推奨機能のマッピング](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)".  
  
## <a name="remarks"></a>解説  
 参照してください[ODBC 64 ビット情報](../../../odbc/reference/odbc-64-bit-information.md)、64 ビット オペレーティング システム、アプリケーションが実行される場合。  
  
> [!NOTE]  
>  ODBC 3.8 で導入された SQL_ASYNC_DBC_FUNCTION_ENABLE 属性はサポートされていません**SQLSetConnectOption**です。 接続ハンドルでの非同期操作を使用するアプリケーションが使用する必要があります**SQLSetConnectAttr**です。  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
