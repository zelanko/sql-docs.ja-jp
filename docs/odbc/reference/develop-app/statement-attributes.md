---
title: ステートメント属性 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQL statements [ODBC], statement attributes
- statement attributes [ODBC]
ms.assetid: 4c59cd8e-a713-4095-9065-20d5bdeafe43
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3bfbfb4647d39a06bc3a722cba9a903815429100
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="statement-attributes"></a>ステートメント属性
ステートメント属性は、ステートメントの特性です。 たとえば、ステートメントの結果で使用するカーソルの設定の種類、ブックマークと新機能を使用するかどうかは、ステートメント属性です。  
  
 ステートメント属性が設定されて**SQLSetStmtAttr**その現在の設定を使用して取得および**SQLGetStmtAttr**です。 アプリケーションが任意のステートメント属性を設定する必要はありません。すべてのステートメント属性では、これらの一部は、ドライバー固有の既定値があります。  
  
 ステートメント属性を設定する場合は、属性自体によって異なります。 ステートメントが実行される前に、SQL_ATTR_CURSOR_TYPE、SQL_ATTR_CONCURRENCY、SQL_ATTR_SIMULATE_CURSOR、および SQL_ATTR_USE_BOOKMARKS ステートメント属性を設定する必要があります。 SQL_ATTR_ASYNC_ENABLE と SQL_ATTR_NOSCAN ステートメント属性は、いつでも設定できますが、ステートメントをもう一度使用まで適用されません。 SQL_ATTR_MAX_LENGTH と SQL_ATTR_MAX_ROWS、SQL_ATTR_QUERY_TIMEOUT のステートメント属性をいつでも設定できますが、ドライバー固有かどうか、ステートメントをもう一度使用する前に適用されます。 残りのステートメント属性は、いつでも設定できます。  
  
> [!NOTE]  
>  呼び出して、接続レベルでのステートメント属性を設定する機能**SQLSetConnectAttr** ODBC 3 では廃止されています*。x*です。 ODBC 3 です。*x*アプリケーションは、接続レベルでステートメント属性を設定しない必要があります。 ODBC 3 です。*x* ODBC 2 で機能する場合、ドライバーはこの機能をサポートのみが必要です*。x*アプリケーションです。 詳細については、次を参照してください。 [SQLSetConnectOption マッピング](../../../odbc/reference/appendixes/sqlsetconnectoption-mapping.md)旧バージョンとの互換性のための付録 g: ドライバーのガイドライン」にします。  
>   
>  この例外は、接続属性とステートメント属性の両方と接続レベルまたはステートメント レベルで設定できます SQL_ATTR_METADATA_ID と SQL_ATTR_ASYNC_ENABLE 属性です。  
>   
>  ODBC 3 で導入された、ステートメント属性でもないです。*x* (SQL_ATTR_METADATA_ID) を除くと、接続レベルで設定できます。  
  
 詳細については、次を参照してください。、 [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)関数の説明。
