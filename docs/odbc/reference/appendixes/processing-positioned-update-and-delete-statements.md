---
title: "処理には、Update および Delete ステートメントが配置されている |Microsoft ドキュメント"
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
- positioned deletes [ODBC]
- ODBC cursor library [ODBC], statement processing
- cursor library [ODBC], positioned update or delete
- positioned updates [ODBC]
- SQL statements [ODBC], cursor library
- ODBC cursor library [ODBC], positioned update or delete
- cursor library [ODBC], statement processing
ms.assetid: 2975dd97-48e6-4d0a-a9c7-40759a7d94c8
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9061ad8221537eaa00eb40fab56fa10d3357198d
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="processing-positioned-update-and-delete-statements"></a>処理には、Update および Delete ステートメントが配置されています。
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないように、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 カーソル ライブラリがサポートする配置されている更新し、置き換えることで delete ステートメント、 **WHERE CURRENT OF**でこのようなステートメントの句、**場所**句のキャッシュに格納されている値を列挙します。各バインドされた列です。 カーソル ライブラリを新しく構築された渡します**更新**と**削除**ステートメントの実行用のドライバーをします。 位置指定の update ステートメントでは、カーソル ライブラリはし、行セットのバッファー内の値からそのキャッシュを更新、SQL_ROW_UPDATED 行の状態配列内の対応する値を設定します。 ステートメントの位置指定削除は、SQL_ROW_DELETED 行の状態配列内の対応する値を設定します。  
  
> [!CAUTION]  
>  **場所**を任意の行を識別する、別の行を特定または複数の行を識別する、現在の行を識別する、カーソル ライブラリで構築された句が失敗します。 詳細については、次を参照してください。[検索ステートメントを構築する](../../../odbc/reference/appendixes/constructing-searched-statements.md)、後の「します。  
  
 配置 update および delete ステートメントは、次の制限の対象では。  
  
-   Update および delete に配置されているステートメントは、次の場合にのみ使用できます: ときに、**選択**ステートメントが結果セットを生成以外の場合、**選択**ステートメントに、結合が含まれていない、 **共用体**句、または**GROUP BY**句; ときに、選択リストで、エイリアスまたは式を使用するすべての列にバインドされていないと**SQLBindCol**です。  
  
-   アプリケーションでは、位置指定の update または delete ステートメントを準備をする場合に行ってください呼び出した後**SQLFetch**または**SQLFetchScroll**です。 カーソル ライブラリを送信すると、ステートメントの準備のドライバーをそのステートメントを終了し、その実行アプリケーションを呼び出すと直接**SQLExecute**です。  
  
-   ドライバーは、1 つだけのアクティブなステートメントをサポートする場合、結果の残りの部分を設定および位置指定を実行する前に、キャッシュから現在の行セットを変わりませんカーソル ライブラリのフェッチを更新または delete ステートメント。 その後、アプリケーションが結果セットのメタデータを返す関数を呼び出す場合 (たとえば、 **SQLNumResultCols**または**SQLDescribeCol**)、カーソル ライブラリには、エラーが返されます。  
  
-   場合、更新プログラムを実行するたびに自動的に更新されるタイムスタンプ列を含むテーブルの列の位置指定更新または削除ステートメントが実行される後続のすべての位置指定更新または削除ステートメントは失敗タイムスタンプ列がある場合バインドされています。 これは、カーソル ライブラリを作成するステートメントが正確には更新する行を識別しません、検索結果を更新または削除するために発生します。 Timestamp 列の検索結果のステートメントで値には、timestamp 列の自動的に更新された値はありません。
