---
title: SQLServerPreparedStatement のメンバー |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2363902f-d4c6-4cd4-a5fc-86079eb9e418
caps.latest.revision: 38
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1926d376ac2653dcc7b4d6b0481bbe968d9469d6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sqlserverpreparedstatement-members"></a>SQLServerPreparedStatement のメンバー
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  次の表に、によって公開されるメンバー、 [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)クラスです。  
  
## <a name="constructors"></a>コンス トラクター  
 [なし] :  
  
## <a name="fields"></a>フィールド  
 [なし] :  
  
## <a name="inherited-fields"></a>継承されたフィールド  
  
|継承元のクラス|メソッド|  
|---------------------------|-------------|  
|java.sql.Statement|CLOSE_ALL_RESULTS、CLOSE_CURRENT_RESULT、EXECUTE_FAILED、KEEP_CURRENT_RESULT、NO_GENERATED_KEYS、RETURN_GENERATED_KEYS、SUCCESS_NO_INFO|  
  
## <a name="methods"></a>メソッド  
  
|名前|Description|  
|----------|-----------------|  
|[addBatch](../../../connect/jdbc/reference/addbatch-method-sqlserverpreparedstatement.md)|このステートメント オブジェクトのコマンド バッチにパラメーターのセットを追加します。|  
|[cancel](../../../connect/jdbc/reference/cancel-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。このステートメントのオブジェクトによって現在実行されている SQL ステートメントを取り消します。|  
|[clearBatch](../../../connect/jdbc/reference/clearbatch-method-sqlserverpreparedstatement.md)|この SQL コマンドの現在のリストを空に[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクト。|  
|[clearParameters](../../../connect/jdbc/reference/clearparameters-method-sqlserverpreparedstatement.md)|現在のパラメーター値を直ちにクリアします。|  
|[clearWarnings](../../../connect/jdbc/reference/clearwarnings-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。このステートメント オブジェクトで報告されるすべての警告をクリアします。|  
|[close](../../../connect/jdbc/reference/close-method-sqlserverpreparedstatement.md)|データベースと JDBC リソースを待たずにすぐに自動的に解放するには、このステートメント オブジェクトの解放します。|  
|[execute](../../../connect/jdbc/reference/execute-method-sqlserverpreparedstatement.md)|SQL ステートメントの任意の種類を指定できます、このステートメント オブジェクトで SQL ステートメントを実行します。|  
|[executeBatch](../../../connect/jdbc/reference/executebatch-method-sqlserverpreparedstatement.md)|実行するコマンド バッチをデータベースに送信します。 すべてのコマンドが正常に実行されている場合は、更新数の配列が返されます。|  
|[さらに executeQuery](../../../connect/jdbc/reference/executequery-method-sqlserverpreparedstatement.md)|このステートメント オブジェクトの SQL クエリを実行しを返します、 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)クエリによって生成されるオブジェクト。|  
|[executeUpdate](../../../connect/jdbc/reference/executeupdate-method-sqlserverpreparedstatement.md)|SQL の INSERT、UPDATE、MERGE、または DELETE ステートメントである必要があります、このステートメント オブジェクトで SQL ステートメントを実行します。または、SQL ステートメントを何も返さない DDL ステートメントなどです。|  
|[getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。取得、 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)ステートメント オブジェクトを生成するオブジェクト。|  
|[getFetchDirection](../../../connect/jdbc/reference/getfetchdirection-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。取得データベース テーブルから行をフェッチする方向は、既定のステートメント オブジェクトから生成された結果セットです。|  
|[getFetchSize](../../../connect/jdbc/reference/getfetchsize-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。結果の既定のフェッチ サイズである結果セットの行の数のセット ステートメント オブジェクトから生成されたオブジェクトを取得します。|  
|[getGeneratedKeys](../../../connect/jdbc/reference/getgeneratedkeys-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。ステートメント オブジェクトを実行した結果作成されるすべての自動生成キーを取得します。|  
|[getMaxFieldSize](../../../connect/jdbc/reference/getmaxfieldsize-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。文字やバイナリ列の値に返されるバイトの最大数を取得、 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)ステートメント オブジェクトによって生成されるオブジェクト。|  
|[getMaxRows](../../../connect/jdbc/reference/getmaxrows-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。行の最大数を取得する、 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)ステートメント オブジェクトによって生成されるオブジェクトを含めることができます。|  
|[getMetaData](../../../connect/jdbc/reference/getmetadata-method-sqlserverpreparedstatement.md)|取得、 [SQLServerResultSetMetaData クラス](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)の列に関する情報を格納しているオブジェクト、 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)ステートメント オブジェクトが実行されたときに返されるオブジェクト。|  
|[getMoreResults](../../../connect/jdbc/reference/getmoreresults-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。このステートメント オブジェクトの次の結果に移動します。|  
|[getParameterMetaData](../../../connect/jdbc/reference/getparametermetadata-method-sqlserverpreparedstatement.md)|数、型、およびステートメント オブジェクトのパラメーターのプロパティを取得します。|  
|[getResponseBuffering](../../../connect/jdbc/reference/getresponsebuffering-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。応答のバッファリング モードを取得[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクト。|  
|[getQueryTimeout](../../../connect/jdbc/reference/getquerytimeout-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。秒数を取得、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]がステートメント オブジェクトの実行を待ちます。|  
|[getResultSet](../../../connect/jdbc/reference/getresultset-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。現在の結果として取得、 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。|  
|[getResultSetConcurrency](../../../connect/jdbc/reference/getresultsetconcurrency-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。結果セットの同時実行を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)ステートメント オブジェクトによって生成されるオブジェクト。|  
|[getResultSetHoldability](../../../connect/jdbc/reference/getresultsetholdability-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。結果セットの保持機能を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)ステートメント オブジェクトによって生成されるオブジェクト。|  
|[getResultSetType](../../../connect/jdbc/reference/getresultsettype-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。結果セットの種類の取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)ステートメント オブジェクトによって生成されるオブジェクト。|  
|[getUpdateCount](../../../connect/jdbc/reference/getupdatecount-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)、)、現在の結果を更新数として取得します。|  
|[getWarnings](../../../connect/jdbc/reference/getwarnings-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。このステートメント オブジェクトの呼び出しによって報告された最初の警告を取得します。|  
|[isClosed](../../../connect/jdbc/reference/isclosed-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。このステートメントのオブジェクトが閉じられたかどうかを示します。|  
|[isPoolable](../../../connect/jdbc/reference/ispoolable-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。ユーザー指定のステートメント プールにステートメントを追加できるかどうかを示す値を返します。|  
|[isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverpreparedstatement.md)|ステートメント オブジェクトが指定されたインターフェイスのラッパーであるかどうかを示します。|  
|[setArray](../../../connect/jdbc/reference/setarray-method-sqlserverpreparedstatement.md)|指定された配列オブジェクトを指定されたパラメーターの数を設定します。|  
|[setAsciiStream](../../../connect/jdbc/reference/setasciistream-method-sqlserverpreparedstatement.md)|指定された InputStream オブジェクトに指定されたパラメーターを設定します。|  
|[setBigDecimal](../../../connect/jdbc/reference/setbigdecimal-method-sqlserverpreparedstatement.md)|指定された BigDecimal オブジェクトに指定されたパラメーターを設定します。|  
|[setBinaryStream](../../../connect/jdbc/reference/setbinarystream-method-sqlserverpreparedstatement.md)|指定されたパラメーターを、指定された入力ストリームに設定します。|  
|[setBlob](../../../connect/jdbc/reference/setblob-method-sqlserverpreparedstatement.md)|指定された Blob オブジェクトに指定されたパラメーターを設定します。|  
|[setboolean](../../../connect/jdbc/reference/setboolean-method-sqlserverpreparedstatement.md)|指定されたパラメーターを指定した設定**ブール**値。|  
|[setByte](../../../connect/jdbc/reference/setbyte-method-sqlserverpreparedstatement.md)|指定されたパラメーターを指定した設定**バイト**値。|  
|[SetBytes](../../../connect/jdbc/reference/setbytes-method-sqlserverpreparedstatement.md)|指定されたパラメーターを、指定された byte 配列に設定します。|  
|[setCharacterStream](../../../connect/jdbc/reference/setcharacterstream-method-sqlserverpreparedstatement.md)|指定された Reader オブジェクトを指定されたパラメーターを設定します。|  
|[setClob](../../../connect/jdbc/reference/setclob-method-sqlserverpreparedstatement.md)|指定された Clob オブジェクトに指定されたパラメーターを設定します。|  
|[setCursorName](../../../connect/jdbc/reference/setcursorname-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。SQL カーソル名を、指定された文字列に設定します。この文字列は、後に続く実行 (execute) メソッドによって使用されます。|  
|[setDate](../../../connect/jdbc/reference/setdate-method-sqlserverpreparedstatement.md)|指定されたパラメーターを、指定された日付の値に設定します。|  
|[setDateTimeOffset](../../../connect/jdbc/reference/setdatetimeoffset-method-sqlserverpreparedstatement.md)|指定された列の値を設定、 [DateTimeOffset クラス](../../../connect/jdbc/reference/datetimeoffset-class.md)値。|  
|[setDouble](../../../connect/jdbc/reference/setdouble-method-sqlserverpreparedstatement.md)|指定されたパラメーターを指定した設定**二重**値。|  
|[setEscapeProcessing](../../../connect/jdbc/reference/setescapeprocessing-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。エスケープの処理モードを設定します。|  
|[setFetchDirection](../../../connect/jdbc/reference/setfetchdirection-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。結果セットの行を処理する方向についてのヒントを JDBC ドライバーに示します。|  
|[setFetchSize](../../../connect/jdbc/reference/setfetchsize-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。さらに行が必要な場合にデータベースからフェッチする必要がある行数について、JDBC ドライバーにヒントを示します。|  
|[setFloat](../../../connect/jdbc/reference/setfloat-method-sqlserverpreparedstatement.md)|指定されたパラメーターを指定した設定**float**値。|  
|[setInt](../../../connect/jdbc/reference/setint-method-sqlserverpreparedstatement.md)|指定されたパラメーターを指定した設定**int**値。|  
|[setLong](../../../connect/jdbc/reference/setlong-method-sqlserverpreparedstatement.md)|指定されたパラメーターを指定した設定**長い**値。|  
|[setMaxFieldSize](../../../connect/jdbc/reference/setmaxfieldsize-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。内のバイトの最大数の上限を設定、 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)文字またはバイナリ値を指定したバイト数を格納する列。|  
|[setMaxRows](../../../connect/jdbc/reference/setmaxrows-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。行の最大数の上限を設定する[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトは、指定した数値を含めることができます。|  
|[setNCharacterStream](../../../connect/jdbc/reference/setncharacterstream-method-sqlserverpreparedstatement.md)|指定された Reader オブジェクトを指定されたパラメーターを設定します。|  
|[setNClob](../../../connect/jdbc/reference/setnclob-method-sqlserverpreparedstatement.md)|指定されたパラメーターを、指定されたオブジェクトに設定します。|  
|[setNull](../../../connect/jdbc/reference/setnull-method-sqlserverpreparedstatement.md)|渡されたパラメーターの型で、指定されたパラメーターを null 値に設定します。|  
|[setNString](../../../connect/jdbc/reference/setnstring-method-int-java-lang-string.md)|指定されたパラメーターを指定した設定**文字列**オブジェクト。|  
|[setObject](../../../connect/jdbc/reference/setobject-method-sqlserverpreparedstatement.md)|指定したオブジェクトを使用して、指定されたパラメーターの値を設定します。|  
|[setPoolable](../../../connect/jdbc/reference/setpoolable-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。ステートメントをプールすること、またはプールしないことを要求します。 既定では、SQLServerPreparedStatement オブジェクトは作成時にプールします。|  
|[setQueryTimeout](../../../connect/jdbc/reference/setquerytimeout-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。ドライバーが指定した秒数を実行するステートメント オブジェクトを待つ秒数を設定します。|  
|[setRef](../../../connect/jdbc/reference/setref-method-sqlserverpreparedstatement.md)|指定された参照オブジェクトを指定されたパラメーターを設定します。|  
|[setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。応答のバッファリング モードを設定[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクト大文字と小文字を**文字列完全**または**アダプティブ**です。|  
|[setShort](../../../connect/jdbc/reference/setshort-method-sqlserverpreparedstatement.md)|指定されたパラメーターを指定した設定**短い**値。|  
|[SetString](../../../connect/jdbc/reference/setstring-method-sqlserverpreparedstatement.md)|指定されたパラメーターを指定した設定**文字列**値。|  
|[setSQLXML](../../../connect/jdbc/reference/setsqlxml-method-sqlserverpreparedstatement.md)|指定されたパラメーターを指定した設定**SQLXML**オブジェクト。|  
|[setTime](../../../connect/jdbc/reference/settime-method-sqlserverpreparedstatement.md)|指定されたパラメーターを、指定された時刻の値に設定します。|  
|[setTimestamp](../../../connect/jdbc/reference/settimestamp-method-sqlserverpreparedstatement.md)|指定されたパラメーターを、指定されたタイムスタンプ値に設定します。|  
|[setUnicodeStream](../../../connect/jdbc/reference/setunicodestream-method-sqlserverpreparedstatement.md)|指定したバイト数が指定された入力ストリームを指定されたパラメーターの数を設定します。|  
|[setURL](../../../connect/jdbc/reference/seturl-method-sqlserverpreparedstatement.md)|指定されたパラメーターを、指定された URL 値に設定します。|  
|[unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverpreparedstatement.md)|アクセス許可を指定したインターフェイスを実装するオブジェクトを返します、 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]-特定のメソッドです。|  
  
## <a name="inherited-methods"></a>継承されたメソッド  
  
|継承元のクラス|メソッド|  
|---------------------------|-------------|  
|com.microsoft.sqlserver.jdbc.SQLServerStatement|cancel、clearWarnings、execute、executeUpdate、getConnection、getFetchDirection、getFetchSize、getGeneratedKeys、getMaxFieldSize、getMaxRows、getMoreResults、getQueryTimeout、getResultSet、getResultSetConcurrency、getResultSetHoldability、getResultSetType、getUpdateCount、getWarnings、isPoolable、setCursorName、setEscapeProcessing、setFetchDirection、setFetchSize、setMaxFieldSize、setMaxRows、setPoolable、setQueryTimeout|  
|java.lang.Object|clone、equals、getClass、hashCode、notify、notifyAll、toString、wait|  
|java.sql.Statement|cancel、clearWarnings、execute、executeUpdate、getConnection、getFetchDirection、getFetchSize、getGeneratedKeys、getMaxFieldSize、getMaxRows、getMoreResults、getQueryTimeout、getResultSet、getResultSetConcurrency、getResultSetHoldability、getResultSetType、getUpdateCount、getWarnings、setCursorName、setEscapeProcessing、setFetchDirection、setFetchSize、setMaxFieldSize、setMaxRows、setQueryTimeout|  
|java.sql.Wrapper|isWrapperFor、unwrap|  
  
## <a name="see-also"></a>参照  
 [SQLServerPreparedStatement クラス](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
