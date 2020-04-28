---
title: ステートメントハンドルを割り当てる ODBC |Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81288432"
---
# <a name="allocating-a-statement-handle-odbc"></a>ステートメント ハンドルの割り当て (ODBC)
アプリケーションでステートメントを実行するには、ステートメントハンドルを次のように割り当てておく必要があります。  
  
1.  アプリケーションは、HSTMT 型の変数を宣言します。 次に、 **SQLAllocHandle**を呼び出し、この変数のアドレス、ステートメントを割り当てる接続のハンドル、および SQL_HANDLE_STMT オプションを渡します。 次に例を示します。  
  
    ```  
    SQLHSTMT hstmt1;  
  
    SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
    ```  
  
2.  ドライバーマネージャーは、ステートメントに関する情報を格納する構造体を割り当て、SQL_HANDLE_STMT オプションを使用してドライバーで**SQLAllocHandle**を呼び出します。  
  
3.  ドライバーは、ステートメントに関する情報を格納する独自の構造体を割り当て、ドライバーマネージャーにドライバーのステートメントハンドルを返します。  
  
4.  ドライバーマネージャーは、アプリケーション変数内のアプリケーションに対する Driver Manager ステートメントハンドルを返します。  
  
 ステートメントハンドルは、ODBC 関数を呼び出すときに使用するステートメントを識別します。 ステートメントハンドルの詳細については、「[ステートメントハンドル](../../../odbc/reference/develop-app/statement-handles.md)」を参照してください。
