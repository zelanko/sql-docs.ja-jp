---
title: カタログデータの利用 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- catalog data [ODBC]
- functions [ODBC], catalog functions
- catalog functions [ODBC], using catalog data
ms.assetid: d5915d0c-eec3-4382-850e-bd863763c99a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 429d42d4a82d0f9f34e33eb4f5f3293100505da9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306813"
---
# <a name="uses-of-catalog-data"></a>カタログ データの使用
アプリケーションは、さまざまな方法でカタログ データを使用します。 一般的な用途を次に示します。  
  
-   **実行時に SQL ステートメントを構築する。** 注文入力アプリケーションなどの垂直アプリケーションには、ハードコーディングされた SQL ステートメントが含まれています。 アプリケーションで使用されるテーブルと列は、これらのテーブルにアクセスするステートメントと同様に、事前に固定されています。 たとえば、注文入力アプリケーションには、通常、システムに新規注文を追加するためのパラメータ化された**INSERT**ステートメントが 1 つ含まれています。  
  
     ODBC を使用してデータを取得するスプレッドシート プログラムなどの汎用アプリケーションは、多くの場合、ユーザーからの入力に基づいて実行時に SQL ステートメントを構築します。 このようなアプリケーションでは、ユーザーが使用するテーブルと列の名前を入力する必要があります。 ただし、アプリケーションがユーザーが選択できるテーブルと列のリストを表示すると、ユーザーにとって簡単です。 これらのリストを作成するには、アプリケーションは**SQLTables**および**SQLColumns**カタログ関数を呼び出します。  
  
-   **開発中に SQL ステートメントを構築する。** アプリケーション開発環境では、通常、プログラマはプログラムの開発中にデータベースクエリを作成できます。 クエリは、ビルドするアプリケーションでハードコーディングされます。  
  
     このような環境では **、SQLTables**と**SQLColumns を**使用して、プログラマが選択できるリストを作成することもできます。 これらの環境では **、SQLPrimaryKeys**と**SQLForeignKeys を**使用して、選択したテーブル間のリレーションシップを自動的に決定および表示し **、SQLStatistics**を使用してインデックス付きフィールドを決定および強調表示し、プログラマが効率的なクエリを作成できるようにします。  
  
-   **カーソルを構築しています。** スクロール可能なカーソル エンジンを提供するアプリケーション、ドライバー、またはミドルウェアは **、SQLSpecialColumns**を使用して、行を一意に識別する列を決定できます。 プログラムは、フェッチされた各行について、これらの列の値を含む*キーセット*を作成できます。 アプリケーションが行に戻ってスクロールすると、これらの値を使用して行の最新データをフェッチします。 スクロール可能なカーソルとキーセットの詳細については、「[スクロール可能なカーソル](../../../odbc/reference/develop-app/scrollable-cursors.md)」を参照してください。
