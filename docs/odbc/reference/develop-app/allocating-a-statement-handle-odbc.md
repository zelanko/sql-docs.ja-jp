---
title: ステートメント ハンドル ODBC の割り当て |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bf9a15bc4622b15afa9838327edd90383a812270
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81288432"
---
# <a name="allocating-a-statement-handle-odbc"></a>ステートメント ハンドルの割り当て (ODBC)
アプリケーションがステートメントを実行するには、次のようにステートメント ハンドルを割り当てる必要があります。  
  
1.  アプリケーションは HSTMT 型の変数を宣言します。 次に **、SQLAllocHandle**を呼び出し、この変数のアドレス、ステートメントを割り当てる接続のハンドル、およびSQL_HANDLE_STMT オプションを渡します。 次に例を示します。  
  
    ```  
    SQLHSTMT hstmt1;  
  
    SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
    ```  
  
2.  ドライバー マネージャーは、ステートメントに関する情報を格納する構造体を割り当てるし、SQL_HANDLE_STMT オプションを使用してドライバーで**SQLAllocHandle**を呼び出します。  
  
3.  ドライバーは、ステートメントに関する情報を格納する独自の構造体を割り当てるドライバー マネージャーにドライバー ステートメント ハンドルを返します。  
  
4.  ドライバー マネージャーは、アプリケーション変数内のアプリケーションにドライバー マネージャーのステートメント ハンドルを返します。  
  
 ステートメント ハンドルは、ODBC 関数を呼び出すときに使用するステートメントを識別します。 ステートメント ハンドルの詳細については、「[ステートメント](../../../odbc/reference/develop-app/statement-handles.md)ハンドル」を参照してください。
