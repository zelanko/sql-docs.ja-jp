---
title: 環境ハンドルの割り当て |Microsoft ドキュメント
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
- ODBC drivers [ODBC], environment handles
- allocating environment handles [ODBC]
- connecting to driver [ODBC], environment handles
- environment handles [ODBC]
- data sources [ODBC], environment handles
- connecting to data source [ODBC], environment handles
- handles [ODBC], environment
ms.assetid: 77b5d1d6-7eb7-428d-bf75-a5c5a325d25c
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0361d97847d7d438af6184f847a065bf5277b0b1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32912147"
---
# <a name="allocating-the-environment-handle"></a>環境ハンドルの割り当てください。
ODBC アプリケーションの最初のタスクが、ドライバー マネージャーの読み込みにはこれを行う方法は、オペレーティング システムに依存します。 たとえば、Microsoft® Windows NT® Server または Windows 2000 Server、Windows NT ワークステーション/Windows 2000 Professional、または Microsoft Windows® 95/98 を実行するコンピューターで、アプリケーションかへのリンク ドライバー マネージャーのライブラリまたは呼び出し**LoadLibrary**ドライバー マネージャーの DLL を読み込めません。  
  
 次のタスクは、アプリケーションが他の ODBC 関数を呼び出す前に行う必要がありますは、ODBC 環境を初期化し、次のように、環境ハンドルを割り当てるには。  
  
1.  アプリケーションでは、型 SQLHENV の変数を宣言します。 呼び出して**SQLAllocHandle**し、この変数と SQL_HANDLE_ENV オプションのアドレスを渡します。 以下に例を示します。  
  
    ```  
    SQLHENV henv1;  
  
    SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv1);  
    ```  
  
2.  ドライバー マネージャーは、環境についての情報を格納する構造体の割り当てし、変数に環境ハンドルを返します。  
  
 ドライバー マネージャーは呼び出しません**SQLAllocHandle**このドライバーで時間を呼び出すには、どのドライバーがわからないためです。 通話を遅延**SQLAllocHandle**アプリケーションがデータ ソースに接続する関数を呼び出すまで、ドライバーでします。 詳細については、次を参照してください。[接続プロセスでドライバー マネージャーの役割](../../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md)、このセクションで後述します。  
  
 環境ハンドルを解放したら、アプリケーションが ODBC を使用して、 **SQLFreeHandle**です。 これは、環境を解放した後、ODBC 関数の呼び出しで、環境のハンドルを使用するアプリケーション プログラミング エラーこれには定義されていないが、おそらく致命的な影響します。  
  
 ときに**SQLFreeHandle**が呼び出されると、ドライバーのリリース環境についての情報を格納する構造体を使用します。 なお**SQLFreeHandle**まで環境ハンドルをその環境ハンドルのすべての接続ハンドルが解放された後に呼び出すことができません。  
  
 環境ハンドルの詳細については、次を参照してください。[環境処理](../../../odbc/reference/develop-app/environment-handles.md)です。
