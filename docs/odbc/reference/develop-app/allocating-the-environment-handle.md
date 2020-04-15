---
title: 環境ハンドルの割り当て |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC drivers [ODBC], environment handles
- allocating environment handles [ODBC]
- connecting to driver [ODBC], environment handles
- environment handles [ODBC]
- data sources [ODBC], environment handles
- connecting to data source [ODBC], environment handles
- handles [ODBC], environment
ms.assetid: 77b5d1d6-7eb7-428d-bf75-a5c5a325d25c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e33b850b2786960a368720deaf89a2203c7dd159
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303005"
---
# <a name="allocating-the-environment-handle"></a>環境ハンドルの割り当て
ODBC アプリケーションの最初のタスクは、ドライバー マネージャーを読み込むことです。これがどのように行われるかは、オペレーティング・システムに依存します。 たとえば、Microsoft® Windows NT® サーバー/Windows 2000 サーバー、Windows NT ワークステーション/Windows 2000 プロフェッショナル、または Microsoft Windows ® 95/98 を実行しているコンピュータでは、このアプリケーションはドライバ マネージャ ライブラリにリンクするか**LoadLibrary**を呼び出してドライバ マネージャ DLL を読み込みます。  
  
 次に、アプリケーションが他の ODBC 関数を呼び出す前に実行する必要があるタスクは、ODBC 環境を初期化し、環境ハンドルを割り当てることです。  
  
1.  アプリケーションは SQLHENV 型の変数を宣言します。 次に **、SQLAllocHandle**を呼び出し、この変数のアドレスとSQL_HANDLE_ENV オプションを渡します。 次に例を示します。  
  
    ```  
    SQLHENV henv1;  
  
    SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv1);  
    ```  
  
2.  ドライバー マネージャーは、環境に関する情報を格納する構造体を割り当てるし、変数に環境ハンドルを返します。  
  
 ドライバー マネージャーは、呼び出すドライバーを知らないので、この時点で、ドライバーで**SQLAllocHandle**を呼び出しません。 アプリケーションがデータ ソースに接続する関数を呼び出すまで、ドライバーで**の SQLAllocHandle**の呼び出しを遅延します。 詳細については、このセクション[の後半の「接続プロセス」の「ドライバー マネージャーの役割](../../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md)」を参照してください。  
  
 アプリケーションが ODBC を使用し終わると **、SQLFreeHandle**を使用して環境ハンドルを解放します。 環境を解放した後は、ODBC 関数の呼び出しで環境のハンドルを使用することは、アプリケーション プログラミング エラーです。そうすることは、未定義だが、おそらく致命的な結果をもたらす。  
  
 **SQLFreeHandle**が呼び出されると、ドライバーは、環境に関する情報を格納するために使用される構造体を解放します。 **SQLFreeHandle**は、その環境ハンドルのすべての接続ハンドルが解放されるまで、環境ハンドルに対して呼び出すことができないことに注意してください。  
  
 環境ハンドルの詳細については、「[環境ハンドル](../../../odbc/reference/develop-app/environment-handles.md)」を参照してください。
