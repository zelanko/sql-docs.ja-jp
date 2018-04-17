---
title: SQLGetData (カーソル ライブラリ) |Microsoft ドキュメント
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
- SQLGetData function [ODBC], Cursor Library
ms.assetid: ff40c9c0-b847-4426-a099-1bff47e6e872
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6b9f9f3217e455d523cbf0740531b5a3c88d1720
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sqlgetdata-cursor-library"></a>SQLGetData (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないように、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックの使用、 **SQLGetData**カーソル ライブラリ内の関数。 に関する一般的な情報**SQLGetData**を参照してください[SQLGetData 関数](../../../odbc/reference/syntax/sqlgetdata-function.md)です。  
  
 カーソル ライブラリを実装する**SQLGetData**最初に構築することによって、**選択**ステートメントを**場所**句の各バインドには、そのキャッシュに格納された値を列挙します。現在の行に列です。 実行して、**選択**し直すには、行グループと呼び出しステートメント**SQLGetData** (キャッシュ) ではなく、データ ソースからデータを取得するドライバー。  
  
> [!CAUTION]  
>  **場所**を任意の行を識別する、別の行を特定または複数の行を識別する、現在の行を識別する、カーソル ライブラリで構築された句が失敗します。 詳細については、次を参照してください。[検索ステートメントを構築する](../../../odbc/reference/appendixes/constructing-searched-statements.md)です。  
  
 SQL_UB_VARIABLE に SQL_ATTR_USE_BOOKMARKS ステートメント属性が設定されている場合**SQLGetData**列 0 ブックマーク データを返すために呼び出すことができます。  
  
 呼び出す**SQLGetData**次の制限が適用されます。  
  
-   **SQLGetData**順方向専用カーソルを呼び出すことができません。  
  
-   **SQLGetData** 、次の条件が満たされたときにのみ呼び出すことができます。**選択**ステートメントには、結果セットが生成された以外の場合は、**選択**ステートメントに、結合が含まれていない、 **共用体**句、または**GROUP BY**句; と、選択リストで、エイリアスまたは式を使用するすべての列にバインドされていない**SQLBindCol**です。  
  
-   カーソル ライブラリが結果を実行する前にセットの残りの部分をフェッチして、ドライバーは、1 つだけのアクティブなステートメントをサポートする場合、**選択**ステートメントと呼び出し元**SQLGetData**です。
