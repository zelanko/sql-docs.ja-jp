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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 80bd4023a0260b67d11d7b4ded1bb810b81e0ab2
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81287352"
---
# <a name="enabling-tracing"></a>トレースの有効化
トレースは、次の3つの方法で有効にすることができます。  
  
-   Odbc .ini レジストリエントリの**Trace**および**tracefile**キーワードを設定します。 SQL_HANDLE_ENV の*Handletype*を使用して**SQLAllocHandle**を呼び出すと、トレースが有効または無効になります。 これらのオプションは、データソースのセットアップ時に表示される [ODBC データソースアドミニストレーター] ダイアログボックスの [トレース] タブで設定します。 詳細については、「[データソースのレジストリエントリ](../../../odbc/reference/install/registry-entries-for-data-sources.md)」を参照してください。  
  
-   **SQLSetConnectAttr**を呼び出して、SQL_ATTR_TRACE 接続属性を SQL_OPT_TRACE_ON に設定します。 これにより、接続中のトレースを有効または無効にすることができます。 詳細については、 [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)関数の説明を参照してください。  
  
-   トレースを動的にオンまたはオフにするには、 **ODBCSharedTraceFlag**を使用します。 (詳細については、次のトピック「[動的トレース](../../../odbc/reference/develop-app/dynamic-tracing.md)」を参照してください)。
