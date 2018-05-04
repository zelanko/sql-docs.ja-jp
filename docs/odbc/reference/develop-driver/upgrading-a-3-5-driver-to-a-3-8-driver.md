---
title: 3.8 ドライバーに 3.5 ドライバーをアップグレードする |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ffba36ac-d22e-40b9-911a-973fa9e10bd3
caps.latest.revision: 27
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 15a97c470d18bab1d5c62e1f2c194ba9f69b20b3
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="upgrading-a-35-driver-to-a-38-driver"></a>3.8 ドライバーに 3.5 ドライバーをアップグレードします。
このトピックでは、ガイドラインと ODBC 3.8 ドライバーに、ODBC 3.5 ドライバーをアップグレードするための考慮事項を示します。  
  
##### <a name="version-numbers"></a>バージョン番号  
 次のガイドラインは、バージョン番号に関連しています。  
  
-   ドライバーは、また、SQL_OV_ODBC2、SQL_OV_ODBC3、および SQL_OV_ODBC3_80 以外の値に対して SQL_ERROR が返されての SQL_OV_ODBC3_80 をサポートする必要があります。 将来のバージョンのドライバー マネージャーは、ドライバーから SQL_SUCCESS が返されます場合に、ドライバーが ODBC 準拠レベルをサポートするいると仮定[SQLSetEnvAttr 関数](../../../odbc/reference/syntax/sqlsetenvattr-function.md)です。  
  
-   バージョン 3.8 ドライバーから 03.80 を返す必要があります**SQLGetInfo** SQL_DRIVER_ODBC_VER に渡されたときに*情報の種類*です。 ただし、古いドライバー マネージャーでは、Microsoft Windows の旧バージョンに含まれていた、ドライバーととして処理 version 3.5 ドライバーでは、警告を発行します。  
  
     Windows 7 では、ドライバー マネージャーのバージョンは、03.80 です。 Windows 8、ドライバー マネージャーのバージョンは SQLGetInfo SQL_DM_VER を介して 03.81 (*情報の種類*パラメーター)。 SQL_ODBC_VER は、Windows 7 および Windows 8 の両方で 03.80 としてバージョンを報告します。  
  
##### <a name="driver-specific-c-data-types"></a>ドライバー固有の C データ型  
 バージョン 3.8 ODBC アプリケーションで使用する場合に、ドライバーが C データ型をカスタマイズしていることができます。 (詳細については、次を参照してください[ODBC における C データ型](../../../odbc/reference/develop-app/c-data-types-in-odbc.md)。)。ただし、3.8 ドライバー、ドライバー固有の C 型を実装するための要件はありません。 ドライバーは C 型の範囲チェックをまだ実行する必要がありますが、ドライバー マネージャーは、操作は実行されませんを 3.8 ドライバー用です。 ドライバーの開発を容易には、次の形式でドライバー固有のもので C データ型の値を定義することができます。  
  
```  
SQL_DRIVER_C_TYPE_BASE+0, SQL_DRIVER_C_TYPE_BASE+1  
```  
  
##### <a name="driver-specific-data-types-descriptor-types-information-types-diagnostic-types-and-attributes"></a>ドライバー固有のデータ型、記述子の種類、情報の種類、診断型、および属性  
 新しいドライバーを開発するときは、データ型、記述子の種類、情報の種類、診断の種類、および属性のドライバー固有の範囲を使用する必要があります。 ドライバー固有の範囲とその基本型の値は、後ほど[ドライバー固有のデータ型、記述子の種類、情報の種類、診断の種類、および属性](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md)です。  
  
##### <a name="connection-pooling"></a>接続のプール  
 接続プールの管理の向上の ODBC 3.8 SQL_ATTR_RESET_CONNECTION 接続属性が導入されています**SQLSetConnectAttr**です。 SQL_RESET_CONNECTION_YES は、この属性の唯一の有効な値です。 ドライバー マネージャーによって接続が接続プールが既定値に、その他の接続属性をリセットするドライバーを許可する前に、SQL_ATTR_RESET_CONNECTION が設定されます。  
  
 サーバーとの不要な通信を防ぐためには、ドライバーは接続がプールから再利用された後、[次へ]、リモート サーバーと通信するまでリセット接続属性を延期できます。  
  
 SQL_ATTR_RESET_CONNECTION がドライバー マネージャーとドライバーの間の通信でのみ使用されるに注意してください。 アプリケーションでは、直接この属性を設定できません。 バージョン 3.8 ドライバーすべてには、この接続属性を実装する必要があります。  
  
##### <a name="streamed-output-parameters"></a>ストリーミングされる出力パラメーター  
 ODBC バージョン 3.8 には、出力パラメーターを取得するストリーミングされる出力パラメーターをスケーラブルな方法が導入されています。 (詳細については、次を参照してください[SQLGetData を使用して出力パラメーターを取得する](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)。)。この機能をサポートするために、ドライバー設定する必要があります SQL_GD_OUTPUT_PARAMS 戻り値の SQL_GETDATA_EXTENSIONS がの場合、*情報の種類*で、 **SQLGetInfo**呼び出します。 ドライバーでは、ストリームの出力パラメーターを持つ SQL の型のサポートを実装しなければなりません。 ドライバー マネージャーでは、無効な SQL 型のエラーは生成されません。 ストリーミングされる出力パラメーターをサポートする SQL 型は、ドライバーで定義されます。  
  
 アプリケーションで使用する場合、ドライバーは SQL_ERROR を返す必要があります**SQLGetData**によって返されるパラメーターと同じではないパラメーターを取得する**SQLParamData**です。  
  
##### <a name="asynchronous-execution-for-connection-operations-polling-method"></a>接続操作 (ポーリング メソッド) の非同期の実行  
 ドライバーは、さまざまな接続の操作の非同期サポートを有効にできます。  
  
 Windows 7 以降では、ODBC では、ポーリング メソッド (詳細については、次を参照してください。[非同期実行 (ポーリング メソッド)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)です。 バージョン 3.8 ODBC ドライバー接続ハンドルで、非同期操作を実装する必要はありません。 ドライバーが、SQL_ASYNC_DBC_FUNCTIONS を実装する必要がありますもドライバーが接続ハンドルで、非同期操作を実装していない場合でも*情報の種類*返す**SQL_ASYNC_DBC_NOT_CAPABLE**です。  
  
 非同期の接続操作を有効にすると、接続の操作の実行時間、繰り返しのすべての呼び出しの合計時間です。 場合は、最後は、呼び出しは実行時間の合計は、SQL_ATTR_CONNECTION_TIMEOUT 接続属性によって設定された値を超えましたされ、操作が完了していないを繰り返し、、ドライバーは SQL_ERROR を返しますと、SQLState HYT01 の診断レコードをログに記録され、。「接続のタイムアウトが期限切れ」のメッセージします。 操作が終了した場合、タイムアウトはありません。  
  
##### <a name="sqlcancelhandle-function"></a>SQLCancelHandle 関数  
 ODBC 3.8 をサポートしている[SQLCancelHandle 関数](../../../odbc/reference/syntax/sqlcancelhandle-function.md)接続とステートメントの両方の操作を取り消すために使用されます。 サポートするドライバー **SQLCancelHandle**関数をエクスポートする必要があります。 ドライバーは、アプリケーションが呼び出す場合の進行状況にある任意の同期または非同期の接続関数をキャンセルしないでください**SQLCancel**または**SQLCancelHandle**ステートメント ハンドルでします。 同様に、ドライバーが進行中のアプリケーションを呼び出す場合は、任意のステートメントが同期または非同期関数をキャンセルしないでください**SQLCancelHandle**接続ハンドルにします。 また、ドライバーが、参照操作をキャンセルしないでください (**SQLBrowseConnect** SQL_NEED_DATA を返します) 場合は、アプリケーションが呼び出す**SQLCancelHandle**接続ハンドルにします。 このような場合は、ドライバーは HY010、「関数のシーケンス エラー」を返す必要があります。  
  
 両方をサポートする必要はありません**SQLCancelHandle**と同時に操作を非同期接続します。 ドライバーは、非同期の接続操作をサポートできますが**SQLCancelHandle**、またはその逆です。  
  
##### <a name="suspended-connections"></a>中断された接続  
 ODBC 3.8 ドライバー マネージャーは、中断状態に接続を配置できます。 アプリケーションが呼び出す**SQLDisconnect**接続に関連付けられているリソースを解放します。 この場合、ドライバーは、接続の状態をチェックせず、できるだけ多くのリソースを解放する試してください。 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。  
  
##### <a name="driver-aware-connection-pooling"></a>ドライバー対応接続プール  
 Windows 8 での ODBC では、接続プールの動作をカスタマイズするドライバーを許可します。 詳細については、次を参照してください。[ドライバー対応接続プール](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)です。  
  
##### <a name="asynchronous-execution-notification-method"></a>非同期実行 (通知方法)  
 ODBC 3.8 は、Windows 8 以降使用できる非同期の操作の通知方法をサポートします。 詳細については、次を参照してください。[非同期実行 (通知方法)](../../../odbc/reference/develop-app/asynchronous-execution-notification-method.md)です。  
  
## <a name="see-also"></a>参照  
 [ODBC ドライバーの開発](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Microsoft 提供の ODBC ドライバー](../../../odbc/microsoft/microsoft-supplied-odbc-drivers.md)   
 [ODBC 3.8 の新機能](../../../odbc/reference/what-s-new-in-odbc-3-8.md)
