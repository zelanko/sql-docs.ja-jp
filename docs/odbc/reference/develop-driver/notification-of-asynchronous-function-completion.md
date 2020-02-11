---
title: 非同期関数完了の通知 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 336565da-4203-4745-bce2-4f011c08e357
author: MightyPen
ms.author: genemi
ms.openlocfilehash: de3496661f2ab329e5bf662a9cb8fa749cb81bfc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68129319"
---
# <a name="notification-of-asynchronous-function-completion"></a>非同期関数の完了の通知
Windows 8 SDK では、非同期操作が完了したときにアプリケーションに通知するメカニズムが ODBC に追加されました。これは、"完了時の通知" として参照されます。 (詳細については、「[非同期実行 (通知方法)](../../../odbc/reference/develop-app/asynchronous-execution-notification-method.md) 」を参照してください)。このトピックでは、ドライバー開発者向けのいくつかの問題について説明します。  
  
## <a name="the-interface-between-the-driver-manager-and-driver"></a>ドライバーマネージャーとドライバーの間のインターフェイス  
 ドライバーマネージャーには、内部的にコールバック関数[Sqlasyncnotificationcallback 関数](../../../odbc/reference/develop-driver/sqlasyncnotificationcallback-function.md)が用意されています。 **Sqlasyncnotificationcallback**は、ドライバーによってのみ呼び出すことができます。アプリケーションは、このコールバックを直接呼び出すことはできません。 最後に SQL_STILL_EXECUTING を返した後、サーバーから新しいデータを受信するたびに、ドライバーは**Sqlasyncnotificationcallback**を呼び出します。  
  
 ドライバーマネージャーはコールバックメカニズムを提供するため、ドライバーは、対応する関数が返された後に非同期操作の実行中に何らかの処理が行われたことをドライバーマネージャーに通知でき SQL_STILL_EXECUTING  
  
 ドライバーマネージャーは、ドライバーの接続ハンドルの SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK 属性を、NULL 以外の関数ポインター (SQL_ASYNC_NOTIFICATION_CALLBACK 型) で設定します。これにより、ドライバーは非同期の通知モードで動作します。そのハンドルに対する操作。 同様に、ドライバーマネージャーは、ドライバーステートメントハンドルの SQL_ATTR_ASYNC_STMT_NOTIFICATION_CALLBACK 属性を NULL 以外の関数ポインター (SQL_ASYNC_NOTIFICATION_CALLBACK 型でもあります) で設定します。これは、ドライバーが通知モードで動作するために使用されます。そのハンドルに対する任意の非同期操作。  
  
 ドライバーハンドルに対して非同期操作を実行する場合、非同期ドライバー関数は非ブロッキングスタイルで動作する必要があります。 操作をすぐに完了できない場合、driver 関数は SQL_STILL_EXECUTING を返します。 この要件は、ポーリングモードと通知モードの両方に当てはまります。  
  
 ハンドルが通知非同期モードの場合、ドライバーは通知コールバック関数を呼び出す必要があります。この関数は、アドレスが SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK または SQL_ATTR_ASYNC_STMT_NOTIFICATION_CALLBACK 属性の値であるため、SQL_STILL_EXECUTING を返します。 つまり、SQL_STILL_EXECUTING を返す1つは、通知コールバック関数の1回の呼び出しとペアにする必要があります。 ドライバーは、SQL_ATTR_ASYNC_DBC_NOTIFICATION_CONTEXT または SQL_ATTR_ASYNC_STMT_NOTIFICATION_CONTEXT handle 属性の現在の値をコールバック関数パラメーター *pContext*の値として使用する必要があります。  
  
 ドライバーは、ドライバー関数を呼び出すスレッドでコールバックすることはできません。関数が戻る前に、進行状況を通知する理由がありません。 ドライバーは、独自のスレッドを使用してコールバックを行う必要があります。 ドライバーマネージャーは、広範な処理ロジックの実行にドライバーのコールバックスレッドを使用しません。  
  
 ドライバーマネージャーは、ドライバーがコールバックした後、元の関数を再度呼び出します。 ドライバーマネージャーは、アプリケーションスレッドでもドライバースレッドでもないスレッドを使用する場合があります。 ドライバーがスレッドに関連付けられている情報 (たとえば、セキュリティトークンやユーザー識別子) を使用する場合、ドライバーは最初の非同期呼び出しで必要な情報を保存し、保存された値を非同期操作全体の前に使用する必要があります。完了. 通常、このような情報を使用する必要があるのは、 **SQLDriverConnect**、 **SQLConnect**、 **SQLBrowseConnect**だけです。  
  
## <a name="see-also"></a>参照  
 [ODBC ドライバーの開発](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)
