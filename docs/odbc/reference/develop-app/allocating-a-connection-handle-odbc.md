---
title: 接続ハンドル ODBC の割り当て |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- allocating connection handles [ODBC]
- data sources [ODBC], connection handles
- connecting to data source [ODBC], connection handles
- ODBC drivers [ODBC], connection handles
- connecting to driver [ODBC], connection handles
- connection handles [ODBC]
- handles [ODBC], connection
ms.assetid: c99a8159-7693-4f97-8dcf-401336550e77
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 12e9f65ee81612e269c1f86ebabd049588443cb8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81288522"
---
# <a name="allocating-a-connection-handle-odbc"></a>接続ハンドルの割り当て (ODBC)
アプリケーションがデータ ソースまたはドライバーに接続する前に、次のように接続ハンドルを割り当てる必要があります。  
  
1.  アプリケーションは、SQLHDBC 型の変数を宣言します。 次に **、SQLAllocHandle**を呼び出し、この変数のアドレス、接続を割り当てる環境のハンドル、およびSQL_HANDLE_DBC オプションを渡します。 次に例を示します。  
  
    ```  
    SQLHDBC hdbc1;  
  
    SQLAllocHandle(SQL_HANDLE_DBC, henv1, &hdbc1);  
    ```  
  
2.  ドライバー マネージャーは、ステートメントに関する情報を格納する構造体を割り当てるし、変数に接続ハンドルを返します。  
  
 ドライバー マネージャーは、呼び出すドライバーを知らないので、この時点で、ドライバーで**SQLAllocHandle**を呼び出しません。 アプリケーションがデータ ソースに接続する関数を呼び出すまで、ドライバーで**の SQLAllocHandle**の呼び出しを遅延します。 詳細については、このセクション[の後半の「接続プロセス」の「ドライバー マネージャーの役割](../../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md)」を参照してください。  
  
 接続ハンドルの割り当ては、ドライバーの読み込みと同じではないことを注意してください。 接続関数が呼び出されるまで、ドライバーは読み込まれません。 したがって、接続ハンドルを割り当てた後、ドライバーまたはデータ ソースに接続する前に、アプリケーションが接続ハンドルで呼び出すことができる唯一の関数は、SQL_ODBC_VER オプションを指定して**SQLSetConnectAttr** **、SQLGetConnectAttr**、または**SQLGetInfo**です。 **SQLEndTran**などの接続ハンドルを使用して他の関数を呼び出すと、SQLSTATE 08003 (接続が開かれていない) が返されます。 詳細については、付録[B: ODBC 状態遷移テーブル](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md)を参照してください。  
  
 接続ハンドルの詳細については、「[接続](../../../odbc/reference/develop-app/connection-handles.md)ハンドル」を参照してください。
