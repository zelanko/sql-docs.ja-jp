---
title: 非同期関数の完了の通知 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 336565da-4203-4745-bce2-4f011c08e357
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a453967f2ffdda4af2a44429737f700f4a994cf8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287822"
---
# <a name="notification-of-asynchronous-function-completion"></a>非同期関数の完了の通知
Windows 8 SDK では、ODBC は、非同期操作が完了したときにアプリケーションに通知するメカニズムを追加しました。 (詳細については[、「非同期実行 (通知方法)」](../../../odbc/reference/develop-app/asynchronous-execution-notification-method.md)を参照してください。このトピックでは、ドライバー開発者向けの問題について説明します。  
  
## <a name="the-interface-between-the-driver-manager-and-driver"></a>ドライバー マネージャーとドライバーの間のインターフェイス  
 ドライバー マネージャーは内部的にコールバック関数[SQLAsync通知コールバック関数](../../../odbc/reference/develop-driver/sqlasyncnotificationcallback-function.md)を提供します。 **SQLAsyncNotificationCallback**は、ドライバーによってのみ呼び出すことができます - アプリケーションは直接呼び出すことはできません。 ドライバーは、最後にSQL_STILL_EXECUTINGを返した後にサーバーから受信した新しいデータを常に**呼**び出します。  
  
 ドライバー マネージャーは、対応する関数が返された後、非同期操作の実行に何らかの進行状況が行われたときにドライバー マネージャーに通知できるように、コールバックのメカニズムを提供SQL_STILL_EXECUTING  
  
 ドライバー マネージャーは、ドライバーの型の型で、ドライバーの接続ハンドルにSQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK属性を設定SQL_ASYNC_NOTIFICATION_CALLBACK、そのハンドルの非同期操作の通知モードで動作します。 同様に、ドライバー マネージャーは、ドライバーのステートメント ハンドルにSQL_ATTR_ASYNC_STMT_NOTIFICATION_CALLBACK属性を設定します、null 以外の関数ポインターも、SQL_ASYNC_NOTIFICATION_CALLBACK型、ドライバーがそのハンドルの非同期操作の通知モードで動作します。  
  
 非同期操作がドライバー ハンドルで実行される場合、非同期ドライバー関数は非ブロックスタイルで動作する必要があります。 操作がすぐに完了できない場合、ドライバー関数はSQL_STILL_EXECUTING返す必要があります。 この要件は、ポーリング モードと通知モードの両方に当てはまります。  
  
 ハンドルが通知非同期モードである場合、ドライバーは、SQL_STILL_EXECUTING返した後、一度、SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACKまたはSQL_ATTR_ASYNC_STMT_NOTIFICATION_CALLBACK属性の値であるアドレスを通知コールバック関数を呼び出す必要があります。 つまり、1 つの戻りSQL_STILL_EXECUTINGは、通知コールバック関数の 1 つの呼び出しとペアにする必要があります。 ドライバーは、コールバック関数パラメーター *pContext*の値として、SQL_ATTR_ASYNC_DBC_NOTIFICATION_CONTEXTまたはハンドル属性の現在の値SQL_ATTR_ASYNC_STMT_NOTIFICATION_CONTEXT使用する必要があります。  
  
 ドライバーは、ドライバー関数を呼び出すスレッドでコールバックすることはできません。関数が戻る前に進行状況を通知する理由はありません。 ドライバーは、コールバックに独自のスレッドを使用する必要があります。 ドライバー マネージャーは、広範な処理ロジックを実行するドライバーのコールバック スレッドを使用しません。  
  
 ドライバー マネージャーは、ドライバーがコールバック後に元の関数を呼び出します。 ドライバー マネージャーは、アプリケーション スレッドでもドライバー のスレッドでもないスレッドを使用できます。 ドライバーは、スレッドに関連付けられている情報を使用する場合 (セキュリティ トークンやユーザー識別子など)、ドライバーは、最初の非同期呼び出しで必要な情報を保存し、全体の非同期操作が完了する前に保存された値を使用する必要があります。 通常、このような情報を使用する必要があるのは **、SQL ドライバ接続** **、SQL 接続**、または**SQLBrowseConnect**のみです。  
  
## <a name="see-also"></a>参照  
 [ODBC ドライバーの開発](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)
