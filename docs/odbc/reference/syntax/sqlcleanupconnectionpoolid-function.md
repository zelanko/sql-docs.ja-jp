---
title: 関数を指定する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLCleanupConnectionPoolID function [ODBC]
ms.assetid: 1fc61908-e003-4587-b91a-32f40569fb99
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a74a92cc05ecd41e99ff87642c7fe3ee527e0c98
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301322"
---
# <a name="sqlcleanupconnectionpoolid-function"></a>SQLCleanupConnectionPoolID 関数
**適合 性**  
 バージョン導入: ODBC 3.81 標準準拠: ODBC  
  
 **まとめ**  
 **プール ID が**タイムアウトしたことをドライバーに通知します。プール ID に関連付けられたプール内のすべての接続がタイムアウトになったときに、プール ID がタイムアウトになる可能性があります。接続タイムアウトの詳細については[、「Microsoft データ アクセス コンポーネントのプール](https://msdn.microsoft.com/library/ms810829.aspx)」を参照してください。  
  
## <a name="syntax"></a>構文  
  
```cpp
  
SQLRETURN  SQLCleanupConnectionPoolID (  
                SQLHENV    EnvironmentHandle  
                SQLPOOLID  PoolID );  
```  
  
## <a name="arguments"></a>引数  
 *環境ハンドル*  
 [入力]プールの環境ハンドル。  
  
 *プール ID*  
 [入力]タイムアウトしたプール ID に関連付けられたプール。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 ドライバー マネージャーは **、SQLCleanupConnectionPoolID**から返される診断情報を処理しません。  
  
 アプリケーションは、ドライバーによって返されるエラー メッセージを受信できません。  
  
## <a name="remarks"></a>解説  
 **いつでも**呼び出すことができますが、ドライバー マネージャーは、他のスレッドが同時に**SQLGetPoolID**を呼び出す必要はなく、そのプール ID に割り当てられた接続情報トークンを使用して**SQLRateConnection**と**SQLPoolConnect**を同時に呼び出しているスレッドがないことを保証します。 したがって、ドライバーは、この関数がスレッド セーフであることを確認する必要があります。  
  
 ドライバーは、プール ID に関連付けられているリソースをクリーンアップできます。  
  
 アプリケーションはこの関数を直接呼び出さないでください。 ドライバー対応接続プールをサポートする ODBC ドライバーは、この関数を実装する必要があります。  
  
 ODBC ドライバ開発用に sqlspi.h を含めます。  
  
## <a name="see-also"></a>参照  
 [ODBC ドライバーの開発](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [ドライバー対応接続プール](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [ODBC ドライバー対応接続プールの開発](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
