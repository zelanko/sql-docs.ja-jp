---
title: トレースの有効化 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- tracing options [ODBC], enabling
ms.assetid: 48e318bd-2487-4708-a698-ea01f36a45e9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fb6d8eaf4a1f4eaadc4e8e9a7030b81c373d8377
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47819920"
---
# <a name="enabling-tracing"></a>トレースの有効化
トレースは、3 つの方法は次で有効にできます。  
  
-   設定、**トレース**と**TraceFile** Odbc.ini のレジストリ エントリに含まれるキーワード。 これを有効またはときにトレースを無効にします**SQLAllocHandle**で、 *HandleType* sql_handle_env としてが呼び出されます。 これらのオプションは、データ ソースのセットアップ中に表示される ODBC データ ソース アドミニストレーター ダイアログ ボックスの トレース タブで設定されます。 詳細については、次を参照してください。[データ ソースのレジストリ エントリ](../../../odbc/reference/install/registry-entries-for-data-sources.md)します。  
  
-   呼び出す**SQLSetConnectAttr** SQL_OPT_TRACE_ON に SQL_ATTR_TRACE 接続属性を設定します。 これを有効または接続の期間のトレースを無効にします。 詳細については、次を参照してください。、 [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)関数の説明。  
  
-   使用**ODBCSharedTraceFlag**トレースをオンまたはオフを動的にします。 (詳細については、次のトピックを参照してください[動的トレース](../../../odbc/reference/develop-app/dynamic-tracing.md)。)。
