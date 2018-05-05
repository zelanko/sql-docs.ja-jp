---
title: トレースの有効化 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- tracing options [ODBC], enabling
ms.assetid: 48e318bd-2487-4708-a698-ea01f36a45e9
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ad1f3aa8fc8280748eb7e3a99a62c500e0b283dd
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="enabling-tracing"></a>トレースを有効にします。
トレースは、3 つの方法では、次に有効ことができます。  
  
-   設定、**トレース**と**TraceFile** Odbc.ini レジストリ エントリに含まれるキーワード。 これを有効または場合にトレースを無効に**SQLAllocHandle**で、 *HandleType* SQL_HANDLE_ENV のと呼びます。 これらのオプションは、データ ソースのセットアップ中に表示される ODBC データ ソース アドミニストレーター ダイアログ ボックスの トレース タブで設定されます。 詳細については、次を参照してください。[データ ソースのレジストリ エントリ](../../../odbc/reference/install/registry-entries-for-data-sources.md)です。  
  
-   呼び出す**SQLSetConnectAttr** SQL_OPT_TRACE_ON に SQL_ATTR_TRACE 接続属性を設定します。 これを有効または接続の期間のトレースを無効にします。 詳細については、次を参照してください。、 [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)関数の説明。  
  
-   使用して**ODBCSharedTraceFlag**トレースをオンまたはオフに動的にします。 (詳細については、次のトピックを参照してください[動的トレース](../../../odbc/reference/develop-app/dynamic-tracing.md)。)。
