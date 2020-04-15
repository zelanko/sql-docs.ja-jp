---
title: トレースを有効にする |マイクロソフトドキュメント
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287352"
---
# <a name="enabling-tracing"></a>トレースの有効化
トレースは、次の 3 つの方法で有効にできます。  
  
-   Odbc.ini レジストリ エントリに**トレース**キーワードと**トレース ファイル**キーワードを設定します。 これにより、*ハンドル型*のSQL_HANDLE_ENVを持つ**SQLAllocHandle**が呼び出されたときにトレースが有効または無効になります。 これらのオプションは、データ ソースのセットアップ中に表示される [ODBC データ ソース アドミニストレータ] ダイアログ ボックスの [トレース] タブで設定します。 詳細については、「[データ ソースのレジストリ エントリ](../../../odbc/reference/install/registry-entries-for-data-sources.md)」を参照してください。  
  
-   接続属性を SQL_OPT_TRACE_ON に設定するには **、SQLSetConnectAttr** SQL_ATTR_TRACE を呼び出します。 これにより、接続の間のトレースが有効または無効になります。 詳細については[、SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)関数の説明を参照してください。  
  
-   トレースを動的にオンまたはオフにするには **、ODBCSharedTraceFlag**を使用します。 (詳細については、次のトピック「[動的トレース](../../../odbc/reference/develop-app/dynamic-tracing.md)」を参照してください)。
