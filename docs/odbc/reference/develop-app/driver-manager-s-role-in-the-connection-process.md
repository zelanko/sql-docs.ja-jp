---
title: ドライバー マネージャー&#39;接続プロセスでの役割 |Microsoft ドキュメント
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
- driver manager [ODBC], role in connection process
- connecting to data source [ODBC], driver manager
- connecting to driver [ODBC], driver manager
- ODBC driver manager [ODBC]
ms.assetid: 77c05630-5a8b-467d-b80e-c705dc06d601
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0ba98332eb196811b71f0cc755f92c84cc9d4091
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32911777"
---
# <a name="driver-manager39s-role-in-the-connection-process"></a>ドライバー マネージャー&#39;接続プロセスでの役割
あるアプリケーション直接呼び出さないでくださいドライバー関数に注意してください。 同じ名前のドライバー マネージャーの関数を呼び出すし、ドライバー マネージャーがドライバー関数を呼び出します。 通常、これはほぼ即座にです。 たとえば、アプリケーションを呼び出す**SQLExecute**ドライバー マネージャーで、いくつかのエラー チェックした後、ドライバー マネージャーは、呼び出し**SQLExecute**ドライバーにします。  
  
 接続プロセスが異なります。 アプリケーションを呼び出すと**SQLAllocHandle** SQL_HANDLE_ENV および sql_handle_dbc としてのオプションが、関数がハンドル ドライバー マネージャーでのみを割り当てます。 ドライバー マネージャーを呼び出すには、どのドライバーがわからないために、ドライバーでは、この関数は呼び出されません。 同様に、アプリケーションがへの接続されていない接続のハンドルを渡すかどうか**SQLSetConnectAttr**または**SQLGetConnectAttr**、のみ、ドライバー マネージャーが、関数を実行します。 格納または取得の接続の属性値を処理し、属性の値を取得するが設定されていないと ODBC の SQLSTATE 08003 (接続が開かれていません) を返しますが、既定値を定義しません。  
  
 アプリケーションを呼び出すと**SQLConnect**、 **SQLDriverConnect**、または**SQLBrowseConnect**、ドライバー マネージャーが最初に使用するドライバーを決定します。 次に、ドライバーが接続で現在読み込まれているかどうかを確認します。  
  
-   接続でドライバーが読み込まれていない場合、ドライバー マネージャーは、同じ環境で他の接続に指定されたドライバーが読み込まれるかどうかを確認します。 かどうか、ドライバー マネージャーを読み込みます。 ドライバーは、接続と呼び出し**SQLAllocHandle** sql_handle_env としてオプションを使用して、ドライバーでします。  
  
     ドライバー マネージャーが、呼び出す**SQLAllocHandle** sql_handle_dbc としてオプションを使用して、ドライバーでかどうかが読み込まれただけです。 ドライバー マネージャーを呼び出す場合は、アプリケーションでは、任意の接続属性を設定、 **SQLSetConnectAttr** ; ドライバーでエラーが発生する場合、ドライバー マネージャーの接続関数を返します SQLSTATE IM006 (ドライバーの**SQLSetConnectAttr**に失敗しました)。 最後に、ドライバー マネージャーは、ドライバーで接続関数を呼び出します。  
  
-   指定されたドライバーが接続で読み込まれている場合、ドライバー マネージャーは、ドライバーで接続関数のみを呼び出します。 この場合、ドライバーは接続上のすべての接続属性がその現在の設定を管理することを確認してください。  
  
-   ドライバー マネージャーを呼び出す場合は、接続で別のドライバーが読み込まれると、 **SQLFreeHandle**ドライバー接続を解放するのです。 ドライバーを使用する他の接続がない場合は、ドライバー マネージャーを呼び出す**SQLFreeHandle**環境を解放するドライバーとドライバーをアンロードします。 ドライバー マネージャーは、ときに、ドライバーが読み込まれていない接続上と同じ操作を実行します。  
  
 ドライバー マネージャーは、環境ハンドルがロックされます (*henv*)、運転免許を呼び出す前に**SQLAllocHandle**と**SQLFreeHandle**とき*HandleType*に設定されている**sql_handle_dbc として**です。  
  
 アプリケーションを呼び出すと**SQLDisconnect**、ドライバー マネージャー呼び出し**SQLDisconnect**ドライバーにします。 ただし、アプリケーションがドライバーに再接続する場合に読み込まれているドライバーに任せます。 アプリケーションを呼び出すと**SQLFreeHandle** sql_handle_dbc としてオプションを使用して、ドライバー マネージャーを呼び出す**SQLFreeHandle**ドライバーにします。 他の接続で、ドライバーを使用しない場合、ドライバー マネージャーは、呼び出し**SQLFreeHandle** sql_handle_env として使用してドライバーのオプションを選択し、ドライバーをアンロードします。
