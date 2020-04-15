---
title: ドライバ マネージャでの関数マッピング |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Unicode [ODBC], functions
- driver manager [ODBC], function mapping
- functions [ODBC], Unicode functions
ms.assetid: ff093b29-671a-4fc0-86c9-08a311a98e54
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: db8e525bb7e8f3e167deb8061a4dd5b75073933c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305583"
---
# <a name="function-mapping-in-the-driver-manager"></a>ドライバー マネージャーの関数マッピング
ドライバー マネージャーは、文字列引数を受け取る関数の 2 つのエントリ ポイントをサポートします。 装飾されていない関数 (**SQLDriverConnect**) は、関数の ANSI 形式です。 ユニコードフォームは*W* **(SQLDriverConnectW**.) で装飾されています。  
  
 ODBC ヘッダー ファイルは、ANSI/Unicode アプリケーションが混在する場合に便利な*A (* **SQLDriverConnectA**) で修飾された関数もサポートしています。 **A**関数への呼び出しは、実際には装飾されていないエントリ ポイント **(SQLDriverConnect**.  
  
 アプリケーションが **_UNICODE#define**でコンパイルされている場合、ODBC ヘッダー ファイルは装飾されていない関数呼び出し (**SQLDriverConnect**) を Unicode バージョン (**SQLDriverConnectW**) にマップします。  
  
 ドライバー マネージャーは、**ドライバーでサポートされている場合は、ドライバー**をユニコード ドライバーとして認識します。  
  
 ドライバーが Unicode ドライバーの場合、ドライバー マネージャーは、次のように関数呼び出しを行います。  
  
-   文字列引数またはパラメーターを指定せずに関数をドライバーに直接渡します。  
  
-   ドライバーに直接 *(W*サフィックスを持つ) Unicode 関数を渡します。  
  
-   文字列引数を Unicode 文字に変換して ANSI 関数 *(A* *W*サフィックスを持つ) を Unicode 関数に変換し、Unicode 関数をドライバーに渡します。  
  
 ドライバーが ANSI ドライバーの場合、ドライバー マネージャーは、次のように関数呼び出しを行います。  
  
-   文字列引数またはパラメーターを指定せずに関数をドライバーに直接渡します。  
  
-   (W サフィックスを持つ) *W* Unicode 関数を ANSI 関数呼び出しに変換し、ドライバーに渡します。  
  
-   ANSI 関数をドライバーに直接渡します。  
  
 ドライバ マネージャは内部的に Unicode 対応です。 その結果、ドライバー マネージャーは、ドライバーに Unicode 関数を渡すだけなので、Unicode ドライバーを使用して、Unicode アプリケーションによって最適なパフォーマンスを得る。 ANSI アプリケーションが ANSI ドライバを使用している場合、ドライバ マネージャは **、SQLDriverConnect**などの一部の関数を処理する際に、文字列を ANSI から Unicode に変換する必要があります。 関数を処理した後、ドライバー マネージャーは、ANSI ドライバーに関数を送信する前に、ANSI に Unicode 文字列を変換する必要があります。  
  
 ドライバーがSQL_STILL_EXECUTINGまたはSQL_NEED_DATAを返すときに、アプリケーションは、バインドされたパラメーター バッファーを変更または読み取る必要があります。 ドライバー マネージャーは、ドライバーがSQL_SUCCESS、SQL_SUCCESS_WITH_INFO、またはSQL_ERRORを返すまで、ANSI にバインドされたバッファーを残します。 マルチスレッド アプリケーションは、別のスレッドが SQL ステートメントを実行しているバインドされたパラメーター値にアクセスできません。 ドライバー マネージャーは、Unicode から ANSI にデータを変換する"イン プレース"、ドライバーがまだ SQL ステートメントを処理中にこれらのバッファー内の ANSI データを参照してください。 Unicode データを ANSI ドライバーにバインドするアプリケーションは、同じアドレスに 2 つの異なる列をバインドする必要があります。
