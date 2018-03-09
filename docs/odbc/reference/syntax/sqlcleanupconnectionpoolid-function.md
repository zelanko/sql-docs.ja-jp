---
title: "SQLCleanupConnectionPoolID 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SQLCleanupConnectionPoolID function [ODBC]
ms.assetid: 1fc61908-e003-4587-b91a-32f40569fb99
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4131ad3555a0206f500b28fc8df7b16a0f4ee707
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="sqlcleanupconnectionpoolid-function"></a>SQLCleanupConnectionPoolID 関数
**準拠**  
 のバージョンで導入されました ODBC 3.81 規格に準拠: ODBC。  
  
 **概要**  
 **SQLCleanupConnectionPoolID**プール ID にタイムアウトになりましたことドライバーに通知します。ID は、そのプール ID に関連付けられたプールのすべての接続されたときに、タイムアウトをことができます、プールがタイムアウトしました。参照してください[Microsoft Data Access Components のプール](http://msdn.microsoft.com/library/ms810829.aspx)接続タイムアウトの詳細についてはします。  
  
## <a name="syntax"></a>構文  
  
```  
SQLRETURN  SQLCleanupConnectionPoolID (  
                SQLHENV    EnvironmentHandle  
                SQLPOOLID  PoolID );  
```  
  
## <a name="arguments"></a>引数  
 *EnvironmentHandle*  
 [入力]プールの環境ハンドルです。  
  
 *PoolID*  
 [入力]タイムアウトするプールの ID に関連付けられたプール。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 ドライバー マネージャーはから返される診断情報を処理しません**SQLCleanupConnectionPoolID**です。  
  
 アプリケーションでは、ドライバーによって返されるエラー メッセージを受信できません。  
  
## <a name="remarks"></a>解説  
 **SQLCleanupConnectionPoolID** 、いつでも呼び出すことができますが、ドライバー マネージャーを他のスレッドが同時を呼び出していないことを保証**SQLGetPoolID**およびその他のスレッドが同時に呼び出しなし**SQLRateConnection**と**SQLPoolConnect**そのプール ID に割り当てられている接続情報のトークンを使用して そのため、ドライバーはこの関数はスレッド セーフであることを確認してください。  
  
 ドライバーはプール ID に関連付けられているリソースをクリーンアップできます。  
  
 アプリケーションでは、この関数を直接呼び出さないでください。 ドライバー対応接続プールをサポートする ODBC ドライバーでは、この関数を実装する必要があります。  
  
 ODBC ドライバーの開発の sqlspi.h が含まれます。  
  
## <a name="see-also"></a>参照  
 [ODBC ドライバーの開発](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [ドライバー対応接続プール](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [ODBC ドライバー対応接続プールの開発](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
