---
title: "関数の非同期完了の通知 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 336565da-4203-4745-bce2-4f011c08e357
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 91c63c55a3d36e1b0c788361a8ae13a01ece9a38
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="notification-of-asynchronous-function-completion"></a>関数の非同期完了の通知
Windows 8 SDK では、ODBC は、非同期操作が完了したら、これを「完了時に通知」と呼びますがアプリケーションに通知するためのメカニズムを追加します。 (を参照してください[非同期実行 (通知方法)](../../../odbc/reference/develop-app/asynchronous-execution-notification-method.md)詳細についてはします)。このトピックでは、ドライバーの開発者の問題の一部を説明します。  
  
## <a name="the-interface-between-the-driver-manager-and-driver"></a>ドライバー マネージャーとドライバーの間のインターフェイス  
 ドライバー マネージャーが内部的にコールバック関数を提供[SQLAsyncNotificationCallback 関数](../../../odbc/reference/develop-driver/sqlasyncnotificationcallback-function.md)です。 **SQLAsyncNotificationCallback**でのみ呼び出せます--ドライバーによってアプリケーション直接呼び出すことはできません。 ドライバー呼び出し**SQLAsyncNotificationCallback**最後返す SQL_STILL_EXECUTING 後に、サーバーから新しいデータ受信するたびにします。  
  
 ドライバー マネージャーがいくつかの進行状況が、対応する関数に SQL_STILL_EXECUTING が返された後に、非同期操作を実行中に加えられた場合に、ドライバーがドライバー マネージャーを通知することができますので、コールバック機構を提供します。  
  
 ドライバー マネージャーは、タイプ SQL_ASYNC_NOTIFICATION_CALLBACK、ドライバーの通知モードで動作するための NULL 以外の関数ポインターを使用して、ドライバーの接続ハンドルの SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK 属性を設定する非同期そのハンドルに対する操作。 ドライバー マネージャーが、これはでも型 SQL_ASYNC_NOTIFICATION_CALLBACK、ドライバーの通知モードで動作するための NULL 以外の関数ポインターを使用してドライバー ステートメント ハンドルで SQL_ATTR_ASYNC_STMT_NOTIFICATION_CALLBACK 属性を設定する同様に、そのハンドルのすべての非同期操作です。  
  
 ドライバーのハンドルで非同期操作を実行すると、非同期ドライバー関数は非ブロッキング スタイルで動作します。 操作が直ちに完了できない場合、ドライバー関数は、SQL_STILL_EXECUTING を返す必要があります。 この要件は、ポーリング モードと通知モードの両方の場合は true です。  
  
 ドライバーが SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK または SQL_ATTR_ASYNC_STMT_NOTIFICATION_CALLBACK 属性の値ですアドレスが、通知のコールバック関数を呼び出す必要があります、ハンドルが通知非同期モードの場合は、後に 1 回。SQL_STILL_EXECUTING が返されます。 つまり、通知のコールバック関数の 1 つの呼び出しに 1 つ返す SQL_STILL_EXECUTING を組み合わせる必要があります。 ドライバーは呼び出しのコールバック関数のパラメーターの値として SQL_ATTR_ASYNC_DBC_NOTIFICATION_CONTEXT または SQL_ATTR_ASYNC_STMT_NOTIFICATION_CONTEXT ハンドルの属性の現在の値を使用する必要があります*pContext*です。  
  
 ドライバーがドライバー関数を呼び出すスレッドで戻る呼び出す必要がありますされません。関数が返す前に、進行状況を通知する必要はありません。 ドライバーは、コールバックに独自のスレッドを使用してください。 ドライバー マネージャーでは、広範な処理ロジックを実行するため、ドライバーのコールバック スレッドは使用しません。  
  
 ドライバー マネージャーは、ドライバーが返信した後に、元の関数を再度呼び出します。 ドライバー マネージャーは、アプリケーション スレッドもドライバーのスレッドにあるスレッドを使用できます。 ドライバー必要があります最初の非同期呼び出しで、必要な情報を保存し、全体の非同期操作の前に保存されている値を使用して、ドライバーは、スレッド (たとえば、セキュリティ トークンまたはユーザー id) に関連付けられている一部の情報を使用している場合完了します。 通常、のみ**SQLDriverConnect**、 **SQLConnect**、または**SQLBrowseConnect**その種の情報を使用する必要があります。  
  
## <a name="see-also"></a>参照  
 [ODBC ドライバーの開発](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)

