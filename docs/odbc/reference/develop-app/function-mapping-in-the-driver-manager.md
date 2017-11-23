---
title: "ドライバー マネージャーでのマッピング機能 |Microsoft ドキュメント"
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
- Unicode [ODBC], functions
- driver manager [ODBC], function mapping
- functions [ODBC], Unicode functions
ms.assetid: ff093b29-671a-4fc0-86c9-08a311a98e54
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 63c908b668e4cecd93cc9930f638ccde9173b563
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="function-mapping-in-the-driver-manager"></a>関数マッピングでは、ドライバー マネージャー
ドライバー マネージャーは、文字列引数を受け取る関数の 2 つのエントリ ポイントをサポートします。 非装飾関数 (**SQLDriverConnect**) 関数の ANSI 形式です。 Unicode フォームが修飾された、 *W* (**SQLDriverConnectW**)。  
  
 ODBC ヘッダー ファイルで修飾された関数もサポートしています、 *A には、* (**SQLDriverConnectA**) 混在 ANSI または Unicode アプリケーションの利便性を考慮します。 呼び出し、 **A**関数は、装飾されていないエントリ ポイントへの呼び出しでは実際には (**SQLDriverConnect**)。  
  
 アプリケーションが、_UNICODE でコンパイルされた場合**#define**、ODBC ヘッダー ファイルは、装飾されていない関数の呼び出しをマップする (**SQLDriverConnect**) を Unicode バージョン (**SQLDriverConnectW**.)  
  
 場合、ドライバー マネージャーで Unicode ドライバーとドライバーが認識**SQLConnectW**ドライバーでサポートされています。  
  
 Unicode、ドライバーには、関数呼び出しがとおり、ドライバー マネージャーは、します。  
  
-   文字列の引数やパラメーターなしの関数をを通じて直接ドライバーに渡します。  
  
-   Unicode 関数に渡します (で、 *W*サフィックス) 経由で直接ドライバーにします。  
  
-   ANSI 関数に変換します (で、 *A*サフィックス) Unicode 関数に (で、 *W*サフィックス) 文字を Unicode に変換される文字列の引数、およびドライバーに、Unicode 関数を渡します。  
  
 ANSI ドライバーをドライバーには、関数呼び出しがとおり、ドライバー マネージャーは、します。  
  
-   文字列の引数または経由で直接パラメーターなしの関数をドライバーに渡します。  
  
-   Unicode 関数に変換 (で、 *W*サフィックス)、ANSI に関数呼び出しと、ドライバーに渡します。  
  
-   ドライバーに直接 ANSI 関数を渡します。  
  
 ドライバー マネージャーが Unicode に対応した内部的にします。 その結果、最適なパフォーマンスは、ドライバー マネージャーでは、ドライバーを通じて Unicode 関数だけが渡されるから Unicode アプリケーションの場合、Unicode のドライバーを使用して取得されます。 使用する場合、ANSI アプリケーションは、ANSI ドライバー、ドライバー マネージャーは、必要があります文字列に変換 ANSI から Unicode など一部の関数の処理時に**SQLDriverConnect**です。 関数を処理した後、ドライバー マネージャー必要がありますし、ANSI に変換する Unicode 文字列戻す関数を ANSI ドライバーに送信する前にします。  
  
 アプリケーションの変更またはドライバーには、SQL_STILL_EXECUTING または SQL_NEED_DATA が返されるときにバインドされたパラメーターにより、バッファーを読み取る必要がありますできません。 ドライバー マネージャーは、ドライバーが SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、または SQL_ERROR に戻るまで、ANSI にバインドされたバッファーを残します。 マルチ スレッド アプリケーションでは、別のスレッドが実行されている SQL ステートメントのバインドされたパラメーター値にアクセスできないようにする必要があります。 ドライバー マネージャーは、データを Unicode から ANSI「インプレース」に変換し、他のスレッド、ドライバーには、SQL ステートメントがまだ処理中にこれらのバッファーに ANSI データが表示可能性があります。 ANSI ドライバーに Unicode データをバインドするアプリケーションは、同じアドレスに 2 つの列をバインドできません必要があります。
