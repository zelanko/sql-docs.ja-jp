---
title: "ODBC 接続ハンドルの割り当て |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- allocating connection handles [ODBC]
- data sources [ODBC], connection handles
- connecting to data source [ODBC], connection handles
- ODBC drivers [ODBC], connection handles
- connecting to driver [ODBC], connection handles
- connection handles [ODBC]
- handles [ODBC], connection
ms.assetid: c99a8159-7693-4f97-8dcf-401336550e77
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 678ba0fa4e256402e9fc25e2e4e60ba4877c6c44
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="allocating-a-connection-handle-odbc"></a>ODBC 接続ハンドルの割り当てください。
アプリケーションは、データ ソースまたはドライバーに接続できるように、ように、接続ハンドルを割り当てますする必要があります。  
  
1.  アプリケーションでは、型 SQLHDBC の変数を宣言します。 呼び出して**SQLAllocHandle**し、この変数は、接続および sql_handle_dbc としてオプションを割り当てるための環境のハンドルのアドレスを渡します。 例:  
  
    ```  
    SQLHDBC hdbc1;  
  
    SQLAllocHandle(SQL_HANDLE_DBC, henv1, &hdbc1);  
    ```  
  
2.  ドライバー マネージャーは、ステートメントの情報を格納する構造体を割り当てるし、変数に、接続ハンドルを返します。  
  
 ドライバー マネージャーは呼び出しません**SQLAllocHandle**このドライバーで時間を呼び出すには、どのドライバーがわからないためです。 通話を遅延**SQLAllocHandle**アプリケーションがデータ ソースに接続する関数を呼び出すまで、ドライバーでします。 詳細については、次を参照してください。[接続プロセスでドライバー マネージャーの役割](../../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md)、このセクションで後述します。  
  
 接続ハンドルの割り当てではありません、ドライバーの読み込みと同じに重要です。 接続の関数が呼び出されるまで、ドライバーが読み込まれていません。 したがって、接続ハンドルの割り当て後と、ドライバーまたはデータ ソースに接続する前に、関数のみが、アプリケーションが接続ハンドルを使用して呼び出すことができますが**SQLSetConnectAttr**、 **SQLGetConnectAttr**、または**SQLGetInfo** SQL_ODBC_VER オプションを使用します。 接続ハンドルを持つその他の関数を呼び出す**SQLEndTran**、SQLSTATE 08003 (接続が開かれていません) を返します。 詳細については、次を参照してください。[付録 b: ODBC 状態遷移表](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md)です。  
  
 接続ハンドルの詳細については、次を参照してください。[接続ハンドル](../../../odbc/reference/develop-app/connection-handles.md)です。

