---
title: ODBC ステートメント ハンドルの割り当て |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], statement handles
- statement handles [ODBC]
- allocating statement handles [ODBC]
- handles [ODBC], statement
ms.assetid: 4ce3b446-34ab-46dc-96e5-f40ec95c267e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9524f2e6b01d2a5827dcface3159b7c52a728c59
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63287868"
---
# <a name="allocating-a-statement-handle-odbc"></a>ステートメント ハンドルの割り当て (ODBC)
アプリケーションがステートメントを実行する前にように、ステートメント ハンドルを割り当てますする必要があります。  
  
1.  アプリケーションは、HSTMT 型の変数を宣言します。 呼び出して**SQLAllocHandle**し、この変数は、ステートメント、および sql_handle_stmt としてオプションを割り当てる接続のハンドルのアドレスを渡します。 以下に例を示します。  
  
    ```  
    SQLHSTMT hstmt1;  
  
    SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
    ```  
  
2.  ドライバー マネージャーは、ステートメントおよび呼び出しに関する情報を格納する構造体を割り当て**SQLAllocHandle** sql_handle_stmt としてオプションを使用してドライバー。  
  
3.  ドライバーは、ステートメントに関する情報を格納するための独自の構造を割り当てるし、ドライバー マネージャーに、ドライバーのステートメント ハンドルを返します。  
  
4.  ドライバー マネージャーは、アプリケーション変数にアプリケーションをドライバー マネージャーのステートメント ハンドルを返します。  
  
 ステートメント ハンドルでは、ODBC 関数を呼び出すときに使用するステートメントを識別します。 ステートメント ハンドルの詳細については、次を参照してください。[ステートメント ハンドル](../../../odbc/reference/develop-app/statement-handles.md)します。
