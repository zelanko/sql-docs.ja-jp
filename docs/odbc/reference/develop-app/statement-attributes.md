---
title: ステートメント属性 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], statement attributes
- statement attributes [ODBC]
ms.assetid: 4c59cd8e-a713-4095-9065-20d5bdeafe43
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0e669f02eeb76ba529c75851ce8bf6ff9a7831a9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47739510"
---
# <a name="statement-attributes"></a>ステートメント属性
ステートメント属性は、ステートメントの特性です。 たとえば、ステートメントの結果を使用するカーソルの設定の種類とブックマークを使用するかどうかは、ステートメントの属性です。  
  
 ステートメント属性が設定されて**SQLSetStmtAttr**で、現在の設定の取得と**SQLGetStmtAttr**します。 アプリケーションで任意のステートメント属性を設定する必要はありません。すべてのステートメント属性では、その一部は、ドライバー固有の既定値があります。  
  
 ステートメント属性を設定する場合は、属性自体に依存します。 ステートメントが実行される前に、SQL_ATTR_CURSOR_TYPE、SQL_ATTR_CONCURRENCY、SQL_ATTR_SIMULATE_CURSOR、および SQL_ATTR_USE_BOOKMARKS ステートメント属性を設定する必要があります。 SQL_ATTR_ASYNC_ENABLE と SQL_ATTR_NOSCAN ステートメント属性は、いつでもでも設定できますが、ステートメントをもう一度使用するまでには適用されません。 SQL_ATTR_MAX_LENGTH と SQL_ATTR_MAX_ROWS、SQL_ATTR_QUERY_TIMEOUT ステートメント属性は、いつでも設定できますが、ドライバー固有かどうか、ステートメントをもう一度使用する前に適用されます。 残りのステートメント属性は、いつでも設定できます。  
  
> [!NOTE]  
>  ステートメント属性を呼び出すことで、接続レベルで設定できる**SQLSetConnectAttr** ODBC 3 では非推奨します *。x*します。 ODBC 3。*x*アプリケーションは接続レベルでステートメント属性を設定しない必要があります。 ODBC 3。*x* ODBC 2 協力する場合、ドライバーはこの機能をサポートのみ必要があります *。x*アプリケーション。 詳細については、[SQLSetConnectOption のマッピング](../../../odbc/reference/appendixes/sqlsetconnectoption-mapping.md)付録 g: ドライバーとの下位互換性のためのガイドラインにを参照してください。  
>   
>  この例外は、これは、接続属性とステートメント属性の両方のいずれかの接続レベルまたはステートメント レベルで設定できます SQL_ATTR_METADATA_ID と SQL_ATTR_ASYNC_ENABLE 属性です。  
>   
>  ODBC 3 で導入された、ステートメント属性の none です。*x* (SQL_ATTR_METADATA_ID) を除くと、接続レベルで設定できます。  
  
 詳細については、次を参照してください。、 [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)関数の説明。
