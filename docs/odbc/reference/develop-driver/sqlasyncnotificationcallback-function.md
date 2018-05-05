---
title: SQLAsyncNotificationCallback 関数 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c56aedc9-f7f7-4641-b605-f0f98ed4400c
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3c785f8547730817c0b1723da38f7ee021aa4f00
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqlasyncnotificationcallback-function"></a>SQLAsyncNotificationCallback 関数
**準拠**  
 バージョンが導入されています。 ODBC 3.8  
  
 標準への準拠: なし  
  
 **概要**  
 **SQLAsyncNotificationCallback**にドライバーをドライバーに SQL_STILL_EXECUTING が返された後に現在の非同期操作のいくつかの進行状況がある場合、ドライバー マネージャーにによるコールバックを許可します。 **SQLAsyncNotificationCallback**だけで、ドライバーによって呼び出されることができます。  
  
 ドライバーは呼び出さないでください**SQLAsyncNotificationCallback**関数の名前を持つ**SQLAsyncNotificationCallback**です。 代わりに、ドライバー マネージャーは、関数ポインターを渡しますドライバー、SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK または SQL_ATTR_ASYNC_STMT_NOTIFICATION_CALLBACK または属性の対応する接続ハンドル、ステートメント ハンドルの値としてそれぞれします。 別のハンドルには、別の関数ポインターの値を割り当てることができます。 関数ポインターの型は、SQL_ASYNC_NOTIFICATION_CALLBACK として定義されます。  
  
 **SQLAsyncNotificationCallback**スレッド セーフです。 複数のスレッドの呼び出しを使用するドライバーが選択できます**SQLAsyncNotificationCallback**でさまざまな処理に同時にします。  
  
## <a name="syntax"></a>構文  
  
```  
typedef SQLRETURN (SQL_API *SQL_ASYNC_NOTIFICATION_CALLBACK)(  
   SQLPOINTER pContex,   
   BOOL fLast);  
```  
  
## <a name="arguments"></a>引数  
 *pContex*  
 ドライバー マネージャーで定義されているデータ構造体へのポインター。 値は、SQLSetConnectAttr(SQL_ATTR_ASYNC_DBC_NOTIFICATION_CONTEXT) または SQLSetStmtAttr(SQL_ATTR_ASYNC_STMT_NOTIFICATION_CONTEXT) を使用して、ドライバーに渡されます。  ドライバーでは、値へのアクセスはありません。  
  
 *fLast*  
 ドライバーを使用すると、このコールバック関数の呼び出しが現在の非同期操作の最後の 1 つであることを示します。 ドライバー マネージャーが、関数をもう一度呼び出すと、ドライバーは SQL_STILL_EXECUTING 以外のリターン コードを返します。 ドライバー マネージャーは、たとえば、この情報を使用して、事前に、アプリケーションは非同期操作の完了を通知するために可能性があります。  
  
 場合*処理*で指定された型の有効なハンドルではありません*HandleType*、 **SQLCancelHandle** SQL_INVALID_HANDLE が返されます。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS や SQL_ERROR です。  
  
## <a name="diagnostics"></a>診断  
 **SQLAsyncNotificationCallback** (これらは、ドライバーまたはドライバー マネージャーの実装の問題を表します次の 2 つの状況の SQL_ERROR を返すことができます。  
  
|[エラー]|Description|  
|-----------|-----------------|  
|接続やステートメントでは、通知は要求されませんでした。||  
|無効な*処理*|ドライバーは、内部のドライバー マネージャーの検証テストに失敗した、無効なハンドルに渡されます。|  
  
## <a name="see-also"></a>参照  
 [非同期実行 (ポーリング メソッド)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)
