---
title: SQL サーバーの参照例 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLBrowseConnect function [ODBC], example
- connecting to data source [ODBC], SqlBrowseConnect
- connecting to driver [ODBC], SQLBrowseConnect
ms.assetid: 6e0d5fd1-ec93-4348-a77a-08f5ba738bc6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7b15aa8e3d573660a312fceb5b9100a41f0384d2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301983"
---
# <a name="sql-server-browsing-example"></a>SQL Server の参照の例
次の例は **、SQLBrowseConnect**を使用して、SQL Server 用のドライバーで使用可能な接続を参照する方法を示しています。 まず、アプリケーションは接続ハンドルを要求します。  
  
```  
SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
```  
  
 次に、アプリケーションは**SQLBrowseConnect**を呼び出し、SQL ドライバによって返されるドライバの説明を使用して、SQL Server**ドライバを指定します**。  
  
```  
SQLBrowseConnect(hdbc, "DRIVER={SQL Server};", SQL_NTS, BrowseResult,  
                  sizeof(BrowseResult), &BrowseResultLen);  
```  
  
 これは**SQLBrowseConnect**への最初の呼び出しであるため、ドライバー マネージャーは、SQL Server ドライバーを読み込み、アプリケーションから受け取ったのと同じ引数を使用してドライバーの**SQLBrowseConnect**関数を呼び出します。  
  
> [!NOTE]  
>  Windows 認証をサポートするデータ ソース プロバイダに接続する場合は、接続文字列`Trusted_Connection=yes`でユーザー ID とパスワード情報の代わりに指定する必要があります。  
  
 ドライバーは、これが**SQLBrowseConnect**への最初の呼び出しであると判断し、接続属性の第 2 レベルを返します: サーバー、ユーザー名、パスワード、アプリケーション名、およびワークステーション ID。 サーバー属性の場合、有効なサーバー名のリストを返します。 **戻**りコードはSQL_NEED_DATA。 参照結果文字列は次のとおりです。  
  
```  
"SERVER:Server={red,blue,green,yellow};UID:Login ID=?;PWD:Password=?;  
   *APP:AppName=?;*WSID:WorkStation ID=?;"  
```  
  
 参照結果文字列の各キーワードの後には、等号の前にコロンと 1 つ以上の単語が続きます。 これらの単語は、アプリケーションがダイアログ ボックスを作成するために使用できるユーザー フレンドリ名です。 **APP**キーワードと**WSID**キーワードには、アスタリスク (省略可能) が付いています。 **SERVER** **、UID、****および PWD**キーワードには、アスタリスクが付きません。値は、次の参照要求文字列で指定する必要があります。 **SERVER**キーワードの値は **、SQLBrowseConnect**によって返されるサーバーのいずれか、またはユーザーが指定した名前のいずれかです。  
  
 アプリケーションは、緑色のサーバーを指定し、**各**キーワードの後に APP キーワードと**WSID**キーワードとユーザー フレンドリ名を省略して **、SQLBrowseConnect**を再度呼び出します。  
  
```  
SQLBrowseConnect(hdbc, "SERVER=green;UID=Smith;PWD=Sesame;", SQL_NTS,  
                  BrowseResult, sizeof(BrowseResult), &BrowseResultLen);  
```  
  
 ドライバが緑色のサーバーに接続を試みます。 キーワードと値のペアがないなどの致命的でないエラーがある場合 **、SQLBrowseConnect**はSQL_NEED_DATAを返し、エラー前と同じ状態を維持します。 アプリケーションは、エラーを判断するために**SQLGetDiagField**または**SQLGetDiagRec**を呼び出すことができます。 接続が成功すると、ドライバはSQL_NEED_DATAを返し、参照結果文字列を返します。  
  
```  
"*DATABASE:Database={master,model,pubs,tempdb};  
   *LANGUAGE:Language={us_english,Franais};"  
```  
  
 この文字列の属性は省略可能なので、アプリケーションは省略できます。 ただし、アプリケーションは、再び**SQLBrowseConnect を**呼び出す必要があります。 アプリケーションがデータベース名と言語を省略することを選択した場合は、空のブラウズ要求文字列を指定します。 この例では、アプリケーションは pubs データベースを選択し、最後に**SQLBrowseConnect**を呼び出し **、DATABASE**キーワードの前に**LANGUAGE**キーワードとアスタリスクを省略します。  
  
```  
SQLBrowseConnect(hdbc, "DATABASE=pubs;", SQL_NTS, BrowseResult,  
                  sizeof(BrowseResult), &BrowseResultLen);  
```  
  
 **DATABASE**属性は、ドライバーが必要とする最終的な接続属性であるため、参照プロセスが完了し、アプリケーションがデータ ソースに接続され **、SQLBrowseConnect**がSQL_SUCCESSを返します。 **また、完全**な接続文字列を参照結果文字列として返します。  
  
```  
"DSN=MySQLServer;SERVER=green;UID=Smith;PWD=Sesame;DATABASE=pubs;"  
```  
  
 ドライバーによって返される最後の接続文字列には、各キーワードの後にユーザー フレンドリ名が含まれていないか、アプリケーションで指定されていないオプションのキーワードが含まれていません。 アプリケーションは、この文字列を**SQLDriverConnect**と共に使用して、現在の接続ハンドルのデータ ソースに再接続するか (切断後)、別の接続ハンドルでデータ ソースに接続できます。 次に例を示します。  
  
```  
SQLDriverConnect(hdbc, hwnd, BrowseResult, SQL_NTS, ConnStrOut,  
                  sizeof(ConnStrOut), &ConnStrOutLen, SQL_DRIVER_NOPROMPT);  
```
