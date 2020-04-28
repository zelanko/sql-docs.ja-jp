---
title: SQLTransact 関数 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLTransact
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLTransact
helpviewer_keywords:
- SQLTransact function [ODBC]
ms.assetid: 496249e0-8eff-4c60-8358-5543bc3ead9c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c7a4f1da36a7c233e9a1b5832ee83e86a5c1f77d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81287082"
---
# <a name="sqltransact-function"></a>SQLTransact 関数
**互換性**  
 導入されたバージョン: ODBC 1.0 標準準拠: 非推奨  
  
 **まとめ**  
 *Odbc 3.x では、* odbc 2.X 関数**Sqltransact**は**SQLEndTran**に置き換えられまし*た。* 詳細については、「 [SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md)」を参照してください。  
  
> [!NOTE]  
>  ODBC 3.8 で導入された属性 SQL_ASYNC_DBC_FUNCTION_ENABLE は、 **Sqltransact**ではサポートされていません。 接続ハンドルで非同期操作を使用するアプリケーションでは、 **SQLEndTran**を使用する必要があります。  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
