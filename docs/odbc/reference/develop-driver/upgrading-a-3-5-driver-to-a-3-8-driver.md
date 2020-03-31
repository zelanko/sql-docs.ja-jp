---
title: 3.5 ドライバを 3.8 ドライバにアップグレードする |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ffba36ac-d22e-40b9-911a-973fa9e10bd3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 97b100b1ade97e1e88cf1421f09a7723412c8b76
ms.sourcegitcommit: 4baa8d3c13dd290068885aea914845ede58aa840
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/13/2020
ms.locfileid: "79289800"
---
# <a name="upgrading-a-35-driver-to-a-38-driver"></a>ドライバー 3.5 をドライバー 3.8 にアップグレードする
このトピックでは、ODBC 3.5 ドライバーを ODBC 3.8 ドライバーにアップグレードするためのガイドラインと考慮事項について説明します。  
  
##### <a name="version-numbers"></a>バージョン番号  
 次のガイドラインはバージョン番号に関連しています。  
  
-   ドライバーは、SQL_OV_ODBC2 SQL_ATTR_ODBC_VERSION、SQL_OV_ODBC3、およびSQL_OV_ODBC3_80以外の値のSQL_ERRORを返すSQL_OV_ODBC3_80をサポートする必要があります。 ドライバー マネージャーの将来のバージョンでは、ドライバーが[SQLSetEnvAttr 関数](../../../odbc/reference/syntax/sqlsetenvattr-function.md)からSQL_SUCCESS返す場合、ドライバーが ODBC 準拠レベルをサポートすることを想定します。  
  
-   バージョン 3.8 のドライバーは *、SQL_DRIVER_ODBC_VERが InfoType*に渡されたときに**SQLGetInfo**から 03.80 を返す必要があります。 ただし、古いバージョンの Microsoft Windows に含まれていた古いドライバー マネージャーは、バージョン 3.5 ドライバーとしてドライバーを扱い、警告を発行します。  
  
     Windows 7 では、ドライバー マネージャーのバージョンは 03.80 です。 Windows 8 では、ドライバー マネージャーのバージョンは、SQLGetInfo SQL_DM_VER *(InfoType*パラメーター) を使用して 03.81 です。 SQL_ODBC_VERは、Windows 7とWindows 8の両方で03.80としてバージョンを報告します。  
  
##### <a name="driver-specific-c-data-types"></a>ドライバ固有の C データ型  
 ドライバーは、バージョン 3.8 ODBC アプリケーションで動作する場合に、カスタマイズされた C データ型を持つことができます。 (詳細については[、ODBC での C データ型を](../../../odbc/reference/develop-app/c-data-types-in-odbc.md)参照してください。ただし、3.8 ドライバーは、ドライバー固有の C 型を実装する必要はありません。 しかし、ドライバーは、C型の範囲チェックを実行する必要があります。ドライバー マネージャーは 3.8 ドライバーの場合は、これを行いません。 ドライバーの開発を容易にする、ドライバー固有の値、C データ型は、次の形式で定義できます。  
  
```  
SQL_DRIVER_C_TYPE_BASE+0, SQL_DRIVER_C_TYPE_BASE+1  
```  
  
##### <a name="driver-specific-data-types-descriptor-types-information-types-diagnostic-types-and-attributes"></a>ドライバー固有のデータ型、記述子の型、情報の種類、診断の種類、および属性  
 新しいドライバーを開発する場合は、データ型、記述子の種類、情報の種類、診断の種類、および属性のドライバー固有の範囲を使用する必要があります。 ドライバー固有の範囲とその基本型の値については[、「ドライバー固有のデータ型、記述子の種類、情報の種類、診断の種類、および属性」で説明します](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md)。  
  
##### <a name="connection-pooling"></a>接続プール  
 接続プールの管理を改善するために、ODBC 3.8 では**SQLSetConnectAttr**のSQL_ATTR_RESET_CONNECTION接続属性が導入されています。 この属性に対して有効な値はSQL_RESET_CONNECTION_YESだけです。 SQL_ATTR_RESET_CONNECTIONは、ドライバー マネージャーが接続プールに接続を配置する直前に設定され、ドライバーは、他の接続属性を既定値にリセットできます。  
  
 サーバーとの不要な通信を避けるために、ドライバーは、接続がプールから再利用された後、リモート サーバーとの次の通信まで、接続属性のリセットを延期できます。  
  
 SQL_ATTR_RESET_CONNECTIONは、ドライバ マネージャとドライバ間の通信でのみ使用されます。 アプリケーションは、この属性を直接設定できません。 バージョン 3.8 のドライバはすべて、この接続属性を実装する必要があります。  
  
##### <a name="streamed-output-parameters"></a>ストリーミング出力パラメータ  
 ODBC バージョン 3.8 では、ストリーム出力パラメーターが導入され、出力パラメーターを取得するためのよりスケーラブルな方法が導入されています。 (詳細については[、「SQLGetData を使用した出力パラメーターの取得](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)」を参照してください)。この機能をサポートするには、**ドライバーは、sqlGetInfo**呼び出しの*InfoType* SQL_GETDATA_EXTENSIONS場合に戻り値にSQL_GD_OUTPUT_PARAMSを設定する必要があります。 ストリーミング出力パラメーターを持つ SQL 型のサポートは、ドライバーで実装する必要があります。 ドライバー マネージャーは、無効な SQL の種類のエラーを生成しません。 ストリーミング出力パラメーターをサポートする SQL 型は、ドライバーで定義されます。  
  
 アプリケーションが SQLGetData を使用して**SQLParamData**によって返されるパラメーターとは別のパラメーターを**SQLParamData**取得する場合、ドライバーはSQL_ERRORを返す必要があります。  
  
##### <a name="asynchronous-execution-for-connection-operations-polling-method"></a>接続操作の非同期実行 (ポーリング メソッド)  
 ドライバーは、さまざまな接続操作の非同期サポートを有効にすることができます。  
  
 Windows 7 以降、ODBC ではポーリング メソッドがサポートされています (詳細については、「[非同期実行 (ポーリング メソッド)」](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)を参照してください。 接続ハンドルに非同期操作を実装するバージョン 3.8 ODBC ドライバーの要件はありません。 ドライバーが接続ハンドルに非同期操作を実装しない場合でも、ドライバーは、SQL_ASYNC_DBC_FUNCTIONS *InfoType*を実装し **、SQL_ASYNC_DBC_NOT_CAPABLE**返す必要があります。  
  
 非同期接続操作が有効な場合、接続操作の実行時間は、すべての繰り返し呼び出しの合計時間になります。 SQL_ATTR_CONNECTION_TIMEOUT接続属性によって設定された値を合計時間が超過した後に最後に繰り返される呼び出しが発生し、操作が完了していない場合、ドライバーはSQL_ERRORを返し、SQLState HYT01 との診断レコードを記録し、メッセージ "接続のタイムアウトが期限切れ" です。 操作が終了してもタイムアウトはありません。  
  
##### <a name="sqlcancelhandle-function"></a>SQLCancelHandle 関数  
 ODBC 3.8 は、接続とステートメントの両方の操作をキャンセルするために使用される[SQLCancelHandle 関数](../../../odbc/reference/syntax/sqlcancelhandle-function.md)をサポートしています。 **SQLCancelHandle**をサポートするドライバーは、関数をエクスポートする必要があります。 アプリケーションがステートメント ハンドルで SQLCancel または**SQLCancelHandle**を呼び出す場合**SQLCancelHandle**、ドライバーは、実行中の同期または非同期の接続関数をキャンセルしないでください。 同様に、アプリケーションが接続ハンドルで**SQLCancelHandle**を呼び出す場合、ドライバーは、実行中の同期または非同期ステートメント関数をキャンセルしないでください。 また、アプリケーションが接続ハンドルで**SQLCancelHandle**を呼び出す場合は、ドライバーは、参照操作をキャンセルしないでください **(SQLBrowseConnect**はSQL_NEED_DATAを返します)。 このような場合、ドライバーは HY010「関数シーケンス エラー」を返す必要があります。  
  
 **SQLCancelHandle**と非同期接続操作の両方を同時にサポートする必要はありません。 ドライバーは、非同期接続操作をサポートできますが **、SQLCancelHandle**をサポートすることはできません。またはその逆も同様です。  
  
##### <a name="suspended-connections"></a>中断された接続  
 ODBC 3.8 ドライバ マネージャは、接続をサスペンド状態にできます。 アプリケーションは**SQLDisconnect**を呼び出して、接続に関連付けられたリソースを解放します。 この場合、ドライバーは、接続の状態を確認せずに、できるだけ多くのリソースを解放しようとする必要があります。 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。  
  
##### <a name="driver-aware-connection-pooling"></a>ドライバー対応接続プール  
 Windows 8 の ODBC では、ドライバーは、接続プールの動作をカスタマイズすることができます。 詳細については、「[ドライバ対応接続プール](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)」を参照してください。  
  
##### <a name="asynchronous-execution-notification-method"></a>非同期実行 (通知方法)  
 ODBC 3.8 では、非同期操作の通知方法がサポートされています。 詳細については、「[非同期実行 (通知メソッド)」](../../../odbc/reference/develop-app/asynchronous-execution-notification-method.md)を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [ODBC ドライバーの開発](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [マイクロソフト提供の ODBC ドライバー](../../../odbc/microsoft/microsoft-supplied-odbc-drivers.md)   
 [ODBC 3.8 の新機能](../../../odbc/reference/what-s-new-in-odbc-3-8.md)
