---
title: "レベル 2 インターフェイスへの準拠 |Microsoft ドキュメント"
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
helpviewer_keywords:
- interface conformance levels [ODBC]
- level 2 interface conformance levels [ODBC]
- conformance levels [ODBC], interface
ms.assetid: 2dc87840-f2fe-43dd-9d7b-bd95523081d9
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 216cfaa83c7b48e94778b98fde9766a47221091b
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="level-2-interface-conformance"></a>レベル 2 インターフェイスへの準拠
インターフェイスへの準拠レベル 2 にはでは、レベル 1 インターフェイスへの準拠レベルの機能と、次の機能が含まれます。  
  
|||  
|-|-|  
|201|データベースのテーブルとビューの 3 部構成の名前を使用します。 (詳細については、2 つの部分から成る名前付けのサポート機能は、101 を参照してください[インターフェイスへの準拠レベル 1](../../../odbc/reference/develop-app/level-1-interface-conformance.md)。)。|  
|202|動的パラメーターを呼び出すことによって記述**SQLDescribeParam**です。|  
|203|だけでなく入力パラメーターも出力パラメーター、入力/出力パラメーター、およびストアド プロシージャの結果の値を使用します。|  
|204|呼び出して、ブックマークの取得を含むブックマークを使用して**SQLDescribeCol**と**SQLColAttribute**列番号が 0 以外の場合は呼び出すことにより、ブックマークに基づくフェッチ**SQLFetchScroll**で、 *FetchOrientation* SQL_FETCH_BOOKMARK; と更新プログラム、設定の引数は、削除、およびブックマーク操作によって呼び出すことによってフェッチ**SQLBulkOperations** で*操作*引数 SQL_UPDATE_BY_BOOKMARK、SQL_DELETE_BY_BOOKMARK、または SQL_FETCH_BY_BOOKMARK に設定します。|  
|205|に関する詳細情報、データ ディクショナリを呼び出して取得**SQLColumnPrivileges**、 **SQLForeignKeys**、および**SQLTablePrivileges**です。|  
|206|呼び出すことによって、その他のデータベース操作を実行する SQL ステートメントではなく ODBC 関数を使用して**SQLBulkOperations** SQL_ADD とまたは**SQLSetPos** SQL_DELETE または SQL_UPDATE にします。 (呼び出しのためにサポート**SQLSetPos**で、 *LockType* SQL_LOCK_EXCLUSIVE または SQL_LOCK_UNLOCK に設定引数がへの準拠レベルの一部ではありませんが、オプション機能です)。|  
|207|指定した個別のステートメントの ODBC 関数の非同期実行を有効にします。|  
|208|呼び出して、テーブルの SQL_ROWVER - 行を識別する列を入手**SQLSpecialColumns**です。 (詳細については、のサポートを参照してください**SQLSpecialColumns**で、 *IdentifierType*引数 SQL_BEST_ROWID 機能の 20 のように設定されて[コア インターフェイス準拠](../../../odbc/reference/develop-app/core-interface-conformance.md)。.)|  
|209|また、ステートメント属性 SQL_ATTR_CONCURRENCY を SQL_CONCUR_READ_ONLY 以外には、少なくとも 1 つの値に設定します。|  
|210|ログイン要求のタイムアウトが発生し、SQL クエリ (SQL_ATTR_LOGIN_TIMEOUT および SQL_ATTR_QUERY_TIMEOUT) する権限です。|  
|211|既定の分離レベルを変更する機能「シリアル化可能な」分離レベルでのトランザクションを実行する権限です。|
