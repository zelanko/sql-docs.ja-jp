---
title: 接続を使用して接続する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connecting to driver [ODBC], SQLBrowseConnect
- SQLBrowseConnect function [ODBC], connecting
- connecting to data source [ODBC], SQLBrowseConnect
ms.assetid: 6c2e9f76-b766-48df-b109-246bb05ae45d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e4d738d394bb3c507f6aa08f736016b51ac4fefb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294662"
---
# <a name="connecting-with-sqlbrowseconnect"></a>SQLBrowseConnect による接続
**SQLBrowseConnect**は、**接続文字列**を使用します。 ただし **、SQLBrowseConnect**を使用すると、アプリケーションは実行時に完全な接続文字列を構築できます。 この方法を使用すると、アプリケーションで次の 2 つのことを行えます。  
  
-   独自のダイアログ ボックスを作成して、この情報を入力するように求めるメッセージを表示し、その "ルック アンド フィール" に対する制御を保持します。  
  
-   特定のドライバーが使用できるデータ ソースをシステムから参照できます。これは複数の手順になる場合があります。 たとえば、ユーザーは最初にネットワークを介してサーバーを参照して、サーバーを選択します。次に、そのサーバーを介して、ドライバーがアクセスできるデータベースを参照するといった手順です。  
  
 アプリケーションは**SQLBrowseConnect**を呼び出し、*参照要求の接続文字列*と呼ばれる、ドライバーまたはデータ ソースを指定する接続文字列を渡します。 ドライバーは、*参照結果の接続文字列*と呼ばれる接続文字列を返します。 アプリケーションは、わかりやすい名前を持つダイアログ ボックスを作成し、値の入力を求めます。 次に、これらの値から新しい参照要求接続文字列を構築し、**これを SQLBrowseConnect**への別の呼び出しでドライバーに返します。  
  
 接続文字列は前後に渡されるため、アプリケーションが古い接続文字列を返すときに新しい接続文字列を返すことで、ドライバーが複数のレベルの参照を提供できます。 たとえば、アプリケーションが**SQLBrowseConnect**を初めて呼び出す場合、ドライバーは、ユーザーにサーバー名を要求するキーワードを返す場合があります。 アプリケーションがサーバー名を返すと、ドライバーは、ユーザーにデータベースの入力を求めるキーワードを返す場合があります。 アプリケーションがデータベース名を返した後で、ブラウズ処理は完了します。  
  
 **SQLBrowseConnect**は、新しい参照結果の接続文字列を返すたびに、リターン コードとしてSQL_NEED_DATAを返します。 これは、接続プロセスが完了していないことをアプリケーションに通知します。 **SQLBrowseConnect**がSQL_SUCCESSを返すまで、接続は必要なデータ状態にあり、接続属性の設定などの他の目的には使用できません。 アプリケーションは **、 SQLDisconnect**を呼び出すことによって接続参照プロセスを終了できます。  
  
 このセクションでは、次のトピックについて説明します。  
  
-   [SQL Server の参照の例](../../../odbc/reference/develop-app/sql-server-browsing-example.md)
