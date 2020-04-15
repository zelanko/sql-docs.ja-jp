---
title: 関数を通知する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: c56aedc9-f7f7-4641-b605-f0f98ed4400c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e6c182c48b8e5ddb70204ddd3a94d9651f97595d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294539"
---
# <a name="sqlasyncnotificationcallback-function"></a>SQLAsyncNotificationCallback 関数
**適合 性**  
 バージョン導入: ODBC 3.8  
  
 標準規格のコンプライアンス: なし  
  
 **まとめ**  
 **SQLAsyncNotificationCallback**ドライバーは、ドライバーがSQL_STILL_EXECUTINGを返した後、現在の非同期操作のいくつかの進行状況がある場合、ドライバー マネージャーにコールバックするドライバーを使用します。 **ドライバー**によってのみ呼び出すことができます。  
  
 ドライバーは、関数名**を**持つ**SQLAsync 通知コールバック**を呼び出しません。 代わりに、ドライバー マネージャーは、対応する接続ハンドルまたはステートメント ハンドルのSQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACKまたはSQL_ATTR_ASYNC_STMT_NOTIFICATION_CALLBACK属性の値としてドライバーに関数ポインターを渡します。 異なるハンドルには、異なる関数ポインター値を割り当てることができます。 関数ポインターの型は、SQL_ASYNC_NOTIFICATION_CALLBACKとして定義されます。  
  
 **コールバック**はスレッド セーフです。 ドライバーは、同時に別のハンドルで**SQLAsyncNotificationCallback を**呼び出す複数のスレッドを使用することを選択できます。  
  
## <a name="syntax"></a>構文  
  
```  
typedef SQLRETURN (SQL_API *SQL_ASYNC_NOTIFICATION_CALLBACK)(  
   SQLPOINTER pContex,   
   BOOL fLast);  
```  
  
## <a name="arguments"></a>引数  
 *pコンテックス*  
 ドライバー マネージャーによって定義されたデータ構造体へのポインター。 値は、SQLSetConnectAttr (SQL_ATTR_ASYNC_DBC_NOTIFICATION_CONTEXT) または SQLSetStmtAttr (SQL_ATTR_ASYNC_STMT_NOTIFICATION_CONTEXT) を介してドライバーに渡されます。  ドライバは値にアクセスできません。  
  
 *ラスト*  
 このコールバック関数の呼び出しが現在の非同期操作の最後の 1 つであることを示すために、ドライバーによって使用されます。 ドライバー マネージャーは、関数を再度呼び出すと、ドライバーはSQL_STILL_EXECUTING以外のリターン コードを返します。 ドライバー マネージャーは、非同期操作が完了することを事前にアプリケーションに通知するなど、この情報を使用する可能性があります。  
  
 *ハンドル*が*ハンドル型*で指定された型の有効なハンドルでない場合は **、SQL_INVALID_HANDLE**を返します。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESSまたはSQL_ERROR。  
  
## <a name="diagnostics"></a>診断  
 **SQLAsyncNotificationCallback**は、次の 2 つの状況 (ドライバーまたはドライバー マネージャーでの実装の問題を示す) のSQL_ERRORを返すことができます。  
  
|エラー|説明|  
|-----------|-----------------|  
|接続またはステートメントは通知を要求しませんでした。||  
|無効な*ハンドル*|ドライバーは、内部ドライバー マネージャーの検証テストに失敗した無効なハンドルで渡されました。|  
  
## <a name="see-also"></a>参照  
 [非同期実行 (ポーリング メソッド)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)
