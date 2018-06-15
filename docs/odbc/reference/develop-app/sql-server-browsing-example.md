---
title: SQL Server の使用例を参照 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLBrowseConnect function [ODBC], example
- connecting to data source [ODBC], SqlBrowseConnect
- connecting to driver [ODBC], SQLBrowseConnect
ms.assetid: 6e0d5fd1-ec93-4348-a77a-08f5ba738bc6
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 113dd18f5ba6c9d2ff8a74e88a920e71bc145893
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32913077"
---
# <a name="sql-server-browsing-example"></a>SQL Server の参照の例
例を次にどのように**SQLBrowseConnect** for SQL Server ドライバーで利用可能な接続を閲覧するために使用する場合があります。 最初に、アプリケーションは、接続ハンドルを要求します。  
  
```  
SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
```  
  
 次に、アプリケーション呼び出し**SQLBrowseConnect**によって返されるドライバーの説明を使用して、SQL Server ドライバーを指定して**SQLDrivers**:  
  
```  
SQLBrowseConnect(hdbc, "DRIVER={SQL Server};", SQL_NTS, BrowseResult,  
                  sizeof(BrowseResult), &BrowseResultLen);  
```  
  
 これは、最初に呼び出すのため**SQLBrowseConnect**、ドライバー マネージャーが、SQL Server ドライバーを読み込むし、ドライバーを呼び出します**SQLBrowseConnect**から受け取った同じ引数を伴う関数、アプリケーション。  
  
> [!NOTE]  
>  Windows 認証をサポートするデータ ソース プロバイダーに接続するかどうかは、する必要がありますを指定する`Trusted_Connection=yes`接続文字列でユーザー ID とパスワード情報の代わりにします。  
  
 ドライバーを決定する最初の呼び出しである**SQLBrowseConnect**し、接続属性の 2 番目のレベルを返します: サーバー、ユーザー名、パスワード、アプリケーション名、およびワークステーション id。 サーバーの属性の有効なサーバー名の一覧を返します。 リターン コード**SQLBrowseConnect** SQL_NEED_DATA がします。 参照の結果の文字列を次に示します。  
  
```  
"SERVER:Server={red,blue,green,yellow};UID:Login ID=?;PWD:Password=?;  
   *APP:AppName=?;*WSID:WorkStation ID=?;"  
```  
  
 参照の結果の文字列の各キーワードは、コロンと等号 (=) の前に 1 つ以上の単語続きます。 これらの単語は、アプリケーションがダイアログ ボックスをビルドに使用できるユーザー フレンドリ名です。 **アプリ**と**WSID**キーワードの先頭には必須では、アスタリスクが付いています。 **サーバー**、 **UID**、および**PWD**キーワード プレフィックスが付いていないアスタリスク;、[次へ] の参照要求の文字列でそれらの値を指定する必要があります。 値、**サーバー**によって返されるサーバーのいずれかのキーワードがあります**SQLBrowseConnect**またはユーザーが指定した名前です。  
  
 アプリケーションの呼び出し**SQLBrowseConnect**もう一度、緑のサーバーの指定を省略すること、**アプリ**と**WSID**キーワードと各キーワードの後に、わかりやすい名前。  
  
```  
SQLBrowseConnect(hdbc, "SERVER=green;UID=Smith;PWD=Sesame;", SQL_NTS,  
                  BrowseResult, sizeof(BrowseResult), &BrowseResultLen);  
```  
  
 ドライバーは、緑色のサーバーに接続しようとします。 不足しているキーワードと値のペアなど、致命的でないエラーがある場合**SQLBrowseConnect** SQL_NEED_DATA が返され、エラーが起こる前と同じ状態のままです。 アプリケーションが呼び出すことができます**SQLGetDiagField**または**SQLGetDiagRec**エラーを確認します。 接続が成功した場合、ドライバーが SQL_NEED_DATA を返し、参照結果の文字列を返します。  
  
```  
"*DATABASE:Database={master,model,pubs,tempdb};  
   *LANGUAGE:Language={us_english,Franais};"  
```  
  
 この文字列内の属性は省略可能であるために、アプリケーションは、これらを省略できます。 ただし、アプリケーションを呼び出す必要があります**SQLBrowseConnect**もう一度です。 アプリケーション選択した場合、データベース名と言語を省略する場合、空の参照要求文字列を指定します。 Pubs データベースとの呼び出しでこの例では、アプリケーションで選択**SQLBrowseConnect**最終的な時点を省略すると、**言語**キーワードと、アスタリスクの前に、**データベース**キーワード。  
  
```  
SQLBrowseConnect(hdbc, "DATABASE=pubs;", SQL_NTS, BrowseResult,  
                  sizeof(BrowseResult), &BrowseResultLen);  
```  
  
 **データベース**属性は、ドライバーで必要な最後の接続属性、参照の処理が完了したら、アプリケーションは、データ ソースに接続し、 **SQLBrowseConnect**関係なく SQL_SUCCESS を返します。 **SQLBrowseConnect**も参照結果の文字列として完全な接続文字列を返します。  
  
```  
"DSN=MySQLServer;SERVER=green;UID=Smith;PWD=Sesame;DATABASE=pubs;"  
```  
  
 ドライバーによって返される最後の接続文字列には、各キーワードの後にわかりやすい名前は含まれません。 また、アプリケーションで指定されていないオプションのキーワードを含んでいるか。 アプリケーションがこの文字列を使用して**SQLDriverConnect** (接続を切断) した後、現在の接続ハンドル上のデータ ソースへの再接続をまたは別の接続ハンドル上のデータ ソースに接続します。 以下に例を示します。  
  
```  
SQLDriverConnect(hdbc, hwnd, BrowseResult, SQL_NTS, ConnStrOut,  
                  sizeof(ConnStrOut), &ConnStrOutLen, SQL_DRIVER_NOPROMPT);  
```
