---
title: カタログ データの使用 |Microsoft ドキュメント
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
ms.topic: conceptual
helpviewer_keywords:
- catalog data [ODBC]
- functions [ODBC], catalog functions
- catalog functions [ODBC], using catalog data
ms.assetid: d5915d0c-eec3-4382-850e-bd863763c99a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bfcb98b9b155f92c88733443e8ce56005faaf0b1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="uses-of-catalog-data"></a>カタログ データの使用
アプリケーションでは、さまざまな方法でカタログ データを使用します。 一般的な使用方法を次に示します。  
  
-   **SQL ステートメントの実行時に作成します。** 、受注アプリケーションなどの垂直方向のアプリケーションでは、ハード コーディングされた SQL ステートメントを含んでいます。 テーブルと、アプリケーションによって使用されている列は固定前もってについては、同様にこれらのテーブルにアクセスするステートメントします。 たとえば、受注アプリケーション通常含まれる 1 つのパラメーター化された**挿入**システムに新しい注文を追加するためのステートメント。  
  
     ODBC を使用して、データを取得するためのスプレッドシート プログラムなどの汎用アプリケーションは、多くの場合、ユーザーからの入力に基づいて実行時に SQL ステートメントを構築します。 このようなアプリケーションには、テーブルおよび使用する列の名前を入力する可能性がありますが必要です。 ただし、できれば、ユーザーを簡単にアプリケーションには、テーブルと、ユーザーが選択をすることが列のリストが表示されます。 これらのリストをビルドすると、アプリケーションが呼び出す、 **SQLTables**と**SQLColumns**カタログ関数。  
  
-   **開発時に SQL ステートメントを構築します。** アプリケーションの開発環境は、通常、プログラムの開発中に、データベース クエリを作成するプログラマを許可します。 クエリは、構築するアプリケーションにハードコーディングなります。  
  
     このような環境が使用も**SQLTables**と**SQLColumns**元となるプログラマ行うことができる選択リストを作成します。 これらの環境を使うことも**SQLPrimaryKeys**と**SQLForeignKeys**自動的に決定して、選択したテーブル間の関係を表示、使用**SQLStatistics**を特定し、プログラマは、効率的なクエリを作成できるように、インデックス付きフィールドを強調表示にします。  
  
-   **カーソルを作成しています。** アプリケーション、ドライバー、または、スクロール可能なカーソル エンジンを提供するミドルウェアを使用でした**SQLSpecialColumns**行を一意に識別する列または列を決定します。 プログラムをビルドでした、*キーセット*フェッチした行ごとにこれらの列の値を格納します。 アプリケーションは、行にスクロールするときに、行の最新のデータをフェッチするのにこれらの値、使用します。 スクロール可能なカーソルおよびキーセットの詳細については、次を参照してください。[スクロール可能なカーソル](../../../odbc/reference/develop-app/scrollable-cursors.md)です。
