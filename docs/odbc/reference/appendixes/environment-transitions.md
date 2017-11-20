---
title: "環境の遷移 |Microsoft ドキュメント"
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
helpviewer_keywords:
- environment transitions [ODBC]
- transitioning states [ODBC], environment
- state transitions [ODBC], environment
ms.assetid: 9d11b1ab-f4c8-48ca-9812-8c04303f939d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a044161df57f81fee3639fd26c94b5860d5c1913
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="environment-transitions"></a>環境の移行
ODBC 環境では、次の 3 つの状態があります。  
  
|状態|Description|  
|-----------|-----------------|  
|E0|未割り当ての環境|  
|E1|割り当てられている環境では、未割り当ての接続|  
|E2|環境では、接続の割り当てください。 の割り当てください。|  
  
 次の表では、各 ODBC 関数が、環境の状態に与える影響を示しています。  
  
## <a name="sqlallochandle"></a>SQLAllocHandle  
  
|E0<br /><br /> 未割り当て|E1<br /><br /> 割り当てられています。|E2<br /><br /> 接続|  
|------------------------|----------------------|-----------------------|  
|E1 [1]|--[4]|--[4]|  
|(組み込み)[2]|E2 [5]<br />(HY010)[6]|--[4]|  
|(組み込み)[3]|(組み込み)|--[4]|  
  
 [1] この行は、移行を示しています。 ときに*HandleType* SQL_HANDLE_ENV をがします。  
  
 [2] この行は、移行を示しています。 ときに*HandleType* sql_handle_dbc としてをがします。  
  
 [3] この行は、移行を示しています。 ときに*HandleType* SQL_HANDLE_STMT または SQL_HANDLE_DESC されました。  
  
 [4] 通話**SQLAllocHandle**で*OutputHandlePtr*そのハンドルの有効なハンドルを指すが上書きされます。 これにより、アプリケーション プログラミング エラー可能性があります。  
  
 [5]、また環境属性は、環境に設定されていました。  
  
 [6]、また環境属性は、環境に設定されていない必要があります。  
  
## <a name="sqldatasources-and-sqldrivers"></a>SQLDataSources と SQLDrivers  
  
|E0<br /><br /> 未割り当て|E1<br /><br /> 割り当てられています。|E2<br /><br /> 接続|  
|------------------------|----------------------|-----------------------|  
|(組み込み)|--[1]<br />(HY010)[2]|--[1]<br />(HY010)[2]|  
  
 [1] で、また環境属性は、環境に設定されていました。  
  
 [2] で、また環境属性は、環境に設定されていない必要があります。  
  
## <a name="sqlendtran"></a>SQLEndTran  
  
|E0<br /><br /> 未割り当て|E1<br /><br /> 割り当てられています。|E2<br /><br /> 接続|  
|------------------------|----------------------|-----------------------|  
|(組み込み)[1]|--[3]<br />(HY010)[4]|--[3]<br />(HY010)[4]|  
|(組み込み)[2]|(組み込み)|--|  
  
 [1] この行は、移行を示しています。 ときに*HandleType* SQL_HANDLE_ENV をがします。  
  
 [2] この行は、移行を示しています。 ときに*HandleType* sql_handle_dbc としてをがします。  
  
 [3] で、また環境属性は、環境に設定されていました。  
  
 [4]、また環境属性は、環境に設定されていない必要があります。  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
  
|E0<br /><br /> 未割り当て|E1<br /><br /> 割り当てられています。|E2<br /><br /> 接続|  
|------------------------|----------------------|-----------------------|  
|(組み込み)[1]|E0|(HY010)|  
|(組み込み)[2]|(組み込み)|--[4]<br />E1 [5]|  
|(組み込み)[3]|(組み込み)|--|  
  
 [1] この行は、移行を示しています。 ときに*HandleType* SQL_HANDLE_ENV をがします。  
  
 [2] この行は、移行を示しています。 ときに*HandleType* sql_handle_dbc としてをがします。  
  
 [3] この行は、移行を示しています。 ときに*HandleType* SQL_HANDLE_STMT または SQL_HANDLE_DESC されました。  
  
 [他の割り当てられていた接続ハンドルが 4] があります。  
  
 [5]、接続ハンドルで指定された*処理*のみ割り当てられていた接続ハンドルがします。  
  
## <a name="sqlgetdiagfield-and-sqlgetdiagrec"></a>SQLGetDiagField と SQLGetDiagRec  
  
|E0<br /><br /> 未割り当て|E1<br /><br /> 割り当てられています。|E2<br /><br /> 接続|  
|------------------------|----------------------|-----------------------|  
|(組み込み)[1]|--|--|  
|(組み込み)[2]|(組み込み)|--|  
  
 [1] この行は、移行を示しています。 ときに*HandleType* SQL_HANDLE_ENV をがします。  
  
 [2] この行は、移行を示しています。 ときに*HandleType* sql_handle_dbc として、sql_handle_stmt として、または SQL_HANDLE_DESC でした。  
  
## <a name="sqlgetenvattr"></a>SQLGetEnvAttr  
  
|E0<br /><br /> 未割り当て|E1<br /><br /> 割り当てられています。|E2<br /><br /> 接続|  
|------------------------|----------------------|-----------------------|  
|(組み込み)|--[1]<br />(HY010)[2]|--|  
  
 [1] で、また環境属性は、環境に設定されていました。  
  
 [2] で、また環境属性は、環境に設定されていない必要があります。  
  
## <a name="sqlsetenvattr"></a>SQLSetEnvAttr  
  
|E0<br /><br /> 未割り当て|E1<br /><br /> 割り当てられています。|E2<br /><br /> 接続|  
|------------------------|----------------------|-----------------------|  
|(組み込み)|--[1]<br />(HY010)[2]|(HY011)|  
  
 [1] で、また環境属性は、環境に設定されていました。  
  
 [2]、*属性*引数が、また、また環境属性が、環境に設定されていません。  
  
## <a name="all-other-odbc-functions"></a>他のすべての ODBC 関数  
  
|E0<br /><br /> 未割り当て|E1<br /><br /> 割り当てられています。|E2<br /><br /> 接続|  
|------------------------|----------------------|-----------------------|  
|(組み込み)|(組み込み)|--|

