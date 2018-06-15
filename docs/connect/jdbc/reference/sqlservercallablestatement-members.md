---
title: SQLServerCallableStatement のメンバー |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: Assembly
ms.assetid: 5ebdc186-e50f-4d14-bbf4-95af5051e4a4
caps.latest.revision: 50
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4efa8910cb11b6cada26afa4ebd034db8aac242c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32852987"
---
# <a name="sqlservercallablestatement-members"></a>SQLServerCallableStatement のメンバー
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  次の表に、によって公開されるメンバー、 [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)クラスです。  
  
## <a name="constructors"></a>コンス トラクター  
 [なし] :  
  
## <a name="fields"></a>フィールド  
  
|継承元のクラス|メソッド|  
|---------------------------|-------------|  
|java.sql.Statement|CLOSE_ALL_RESULTS、CLOSE_CURRENT_RESULT、EXECUTE_FAILED、KEEP_CURRENT_RESULT、NO_GENERATED_KEYS、RETURN_GENERATED_KEYS、SUCCESS_NO_INFO|  
  
## <a name="inherited-fields"></a>継承されたフィールド  
 [なし] :  
  
## <a name="methods"></a>メソッド  
  
|名前|Description|  
|----------|-----------------|  
|[addBatch](../../../connect/jdbc/reference/addbatch-method-sqlserverpreparedstatement.md)|(から継承された[SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md))。CallableStatement オブジェクトに対するコマンドのバッチにパラメーターのセットを追加します。|  
|[cancel](../../../connect/jdbc/reference/cancel-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。この CallableStatement オブジェクトによって現在実行されている SQL ステートメントを取り消します。|  
|[clearBatch](../../../connect/jdbc/reference/clearbatch-method-sqlserverpreparedstatement.md)|(から継承された[SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md))。現在この CallableStatement オブジェクトに対する SQL コマンドの一覧を空にします。|  
|[clearParameters](../../../connect/jdbc/reference/clearparameters-method-sqlserverpreparedstatement.md)|(から継承された[SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md))。現在のパラメーター値を直ちにクリアします。|  
|[clearWarnings](../../../connect/jdbc/reference/clearwarnings-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。この CallableStatement オブジェクトについて報告されたすべての警告をクリアします。|  
|[close](../../../connect/jdbc/reference/close-method-sqlserverpreparedstatement.md)|(から継承された[SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md))。データベースと JDBC リソースを待たずにすぐに自動的に解放するには、この CallableStatement オブジェクトの解放します。|  
|[execute](../../../connect/jdbc/reference/execute-method-sqlserverpreparedstatement.md)|(から継承された[SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md))。SQL ステートメントの任意の種類を指定できます、この CallableStatement オブジェクトで SQL ステートメントを実行します。|  
|[executeBatch](../../../connect/jdbc/reference/executebatch-method-sqlserverpreparedstatement.md)|(から継承された[SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md))。実行するコマンド バッチをデータベースに送信します。 すべてのコマンドが正常に実行されている場合は、更新数の配列が返されます。|  
|[さらに executeQuery](../../../connect/jdbc/reference/executequery-method-sqlserverpreparedstatement.md)|(から継承された[SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md))。この CallableStatement オブジェクトの SQL クエリを実行しを返します、 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)クエリによって生成されるオブジェクト。|  
|[executeUpdate](../../../connect/jdbc/reference/executeupdate-method-sqlserverpreparedstatement.md)|(から継承された[SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md))。SQL の INSERT、UPDATE、MERGE、または DELETE ステートメントである必要があります、この CallableStatement オブジェクトで SQL ステートメントを実行します。または、SQL ステートメントを何も返さない DDL ステートメントなどです。|  
|[getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。取得、 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)この CallableStatement オブジェクトを生成したオブジェクト。|  
|[getDateTimeOffset](../../../connect/jdbc/reference/getdatetimeoffset-method-sqlservercallablestatement.md)|指定した列の値を取得、 [DateTimeOffset クラス](../../../connect/jdbc/reference/datetimeoffset-class.md)オブジェクト。|  
|[getFetchDirection](../../../connect/jdbc/reference/getfetchdirection-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。取得データベース テーブルから行をフェッチする方向は、既定のこの CallableStatement オブジェクトから生成される結果セットです。|  
|[getFetchSize](../../../connect/jdbc/reference/getfetchsize-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。結果の既定のフェッチ サイズである結果セットの行の数のセットこの CallableStatement オブジェクトから生成されたオブジェクトを取得します。|  
|[getGeneratedKeys](../../../connect/jdbc/reference/getgeneratedkeys-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。CallableStatement オブジェクトを実行した結果作成されるすべての自動生成キーを取得します。|  
|[getMaxFieldSize](../../../connect/jdbc/reference/getmaxfieldsize-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。文字やバイナリ列の値に返されるバイトの最大数を取得、 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) CallableStatement オブジェクトによって生成されるオブジェクト。|  
|[getMaxRows](../../../connect/jdbc/reference/getmaxrows-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。行の最大数を取得する、 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) CallableStatement オブジェクトによって生成されるオブジェクトを含めることができます。|  
|[getMetaData](../../../connect/jdbc/reference/getmetadata-method-sqlserverpreparedstatement.md)|(から継承された[SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md))。取得、 [SQLServerResultSetMetaData クラス](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)の列に関する情報を格納しているオブジェクト、 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)この CallableStatement オブジェクトの実行時に返されるオブジェクト。|  
|[getMoreResults](../../../connect/jdbc/reference/getmoreresults-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。この CallableStatement オブジェクトの次の結果に移動します。|  
|[getParameterMetaData](../../../connect/jdbc/reference/getparametermetadata-method-sqlserverpreparedstatement.md)|(から継承された[SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md))。数、型、および CallableStatement オブジェクトのパラメーターのプロパティを取得します。|  
|[getArray](../../../connect/jdbc/reference/getarray-method-sqlservercallablestatement.md)|配列オブジェクトとして指定されたパラメーターの値を取得します。|  
|[getAsciiStream](../../../connect/jdbc/reference/getasciistream-method-sqlservercallablestatement.md)|指定されたパラメーターの値のストリームとして取得**ASCII**文字です。|  
|[getBigDecimal](../../../connect/jdbc/reference/getbigdecimal-method-sqlservercallablestatement.md)|指定されたパラメーターの値を java.math.BigDecimal として取得します。|  
|[getBinaryStream](../../../connect/jdbc/reference/getbinarystream-method-sqlservercallablestatement.md)|指定されたパラメーターの値を連続するバイトのバイナリ ストリームとして取得します。|  
|[GetBlob](../../../connect/jdbc/reference/getblob-method-sqlservercallablestatement.md)|指定された JDBC Blob パラメーターの値を Java プログラミング言語では、Blob オブジェクトとして取得します。|  
|[getboolean](../../../connect/jdbc/reference/getboolean-method-sqlservercallablestatement.md)|として指定されたパラメーターの値を取得、**ブール**値。|  
|[GetByte](../../../connect/jdbc/reference/getbyte-method-sqlservercallablestatement.md)|として指定されたパラメーターの値を取得、**バイト**値。|  
|[GetBytes](../../../connect/jdbc/reference/getbytes-method-sqlservercallablestatement.md)|指定されたパラメーターの値を byte 配列として取得します。|  
|[getCharacterStream](../../../connect/jdbc/reference/getcharacterstream-method-sqlservercallablestatement.md)|指定されたパラメーターの値を java.io.Reader オブジェクトとして取得します。|  
|[getClob](../../../connect/jdbc/reference/getclob-method-sqlservercallablestatement.md)|指定された JDBC Blob パラメーターの値を Java プログラミング言語では、Clob オブジェクトとして取得します。|  
|[getDate](../../../connect/jdbc/reference/getdate-method-sqlservercallablestatement.md)|指定されたパラメーターの値を Java プログラミング言語の java.sql.Date オブジェクトとして取得します。|  
|[getDateTimeOffset](../../../connect/jdbc/reference/getdatetimeoffset-method-sqlservercallablestatement.md)|指定した列の値を取得、[DateTimeOffset クラス](../../../connect/jdbc/reference/datetimeoffset-class.md)オブジェクト。|  
|[GetDouble](../../../connect/jdbc/reference/getdouble-method-sqlservercallablestatement.md)|として指定されたパラメーターの値を取得、**二重**java プログラミング言語です。|  
|[GetFloat](../../../connect/jdbc/reference/getfloat-method-sqlservercallablestatement.md)|として指定されたパラメーターの値を取得、 **float** java プログラミング言語です。|  
|[getInt](../../../connect/jdbc/reference/getint-method-sqlservercallablestatement.md)|として指定されたパラメーターの値を取得、 **int** java プログラミング言語です。|  
|[getLong](../../../connect/jdbc/reference/getlong-method-sqlservercallablestatement.md)|として指定されたパラメーターの値を取得、**長い**java プログラミング言語です。|  
|[getNCharacterStream](../../../connect/jdbc/reference/getncharacterstream-method-sqlservercallablestatement.md)|リーダー オブジェクトとして指定されたパラメーターの値を取得します。|  
|[getNClob](../../../connect/jdbc/reference/getnclob-method-sqlservercallablestatement.md)|指定された JDBC の値を取得**NCLOB**パラメーターとして、 **NClob** Java プログラミング言語のオブジェクト。|  
|[getNString](../../../connect/jdbc/reference/getnstring-method-sqlservercallablestatement.md)|指定された値を取得**NCHAR**、 **NVARCHAR**または**LONGNVARCHAR** Java プログラミング言語の文字列としてのパラメーターです。|  
|[GetObject](../../../connect/jdbc/reference/getobject-method-sqlservercallablestatement.md)|指定されたパラメーターの値を Java プログラミング言語のオブジェクトとして取得します。|  
|[getQueryTimeout](../../../connect/jdbc/reference/getquerytimeout-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。秒数を取得、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]は CallableStatement オブジェクトの実行を待ちます。|  
|[getRef](../../../connect/jdbc/reference/getref-method-sqlservercallablestatement.md)|指定されたパラメーターの値を Java プログラミング言語では、Ref オブジェクトとして取得します。|  
|[getResponseBuffering](../../../connect/jdbc/reference/getresponsebuffering-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。応答のバッファリング モードを取得[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクト。|  
|[getResultSet](../../../connect/jdbc/reference/getresultset-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。現在の結果として取得、 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。|  
|[getResultSetConcurrency](../../../connect/jdbc/reference/getresultsetconcurrency-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。結果セットの同時実行を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) CallableStatement オブジェクトによって生成されるオブジェクト。|  
|[getResultSetHoldability](../../../connect/jdbc/reference/getresultsetholdability-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。結果セットの保持機能を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) CallableStatement オブジェクトによって生成されるオブジェクト。|  
|[getResultSetType](../../../connect/jdbc/reference/getresultsettype-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。結果セットの種類の取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) CallableStatement オブジェクトによって生成されるオブジェクト。|  
|[getShort](../../../connect/jdbc/reference/getshort-method-sqlservercallablestatement.md)|として指定されたパラメーターの値を取得、**短い**java プログラミング言語です。|  
|[GetString](../../../connect/jdbc/reference/getstring-method-sqlservercallablestatement.md)|として指定されたパラメーターの値を取得、**文字列**java プログラミング言語です。|  
|[getSQLXML](../../../connect/jdbc/reference/getsqlxml-method-sqlservercallablestatement.md)|指定されたパラメーターの値を java.sql.SQLXML オブジェクトとして取得します。|  
|[getTime](../../../connect/jdbc/reference/gettime-method-sqlservercallablestatement.md)|指定されたパラメーターの値を Java プログラミング言語の java.sql.Time オブジェクトとして取得します。|  
|[getTimestamp](../../../connect/jdbc/reference/gettimestamp-method-sqlservercallablestatement.md)|指定されたパラメーターの値を Java プログラミング言語の java.sql.Timestamp オブジェクトとして取得します。|  
|[getUpdateCount](../../../connect/jdbc/reference/getupdatecount-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。現在の結果を更新数として取得します。|  
|[getURL](../../../connect/jdbc/reference/geturl-method-sqlservercallablestatement.md)|指定されたパラメーターの値を Java プログラミング言語で URL オブジェクトとして取得します。|  
|[getWarnings](../../../connect/jdbc/reference/getwarnings-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。この CallableStatement オブジェクトの呼び出しによって報告された最初の警告を取得します。|  
|[isClosed](../../../connect/jdbc/reference/isclosed-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。このステートメントのオブジェクトが閉じられたかどうかを示します。|  
|[isPoolable](../../../connect/jdbc/reference/ispoolable-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。ユーザー指定のステートメント プールにステートメントを追加できるかどうかを示す値を返します。|  
|[isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlservercallablestatement.md)|ステートメント オブジェクトが指定されたインターフェイスのラッパーであるかどうかを示します。|  
|[registerOutParameter](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md)|OUT パラメーターを登録します。|  
|[setArray](../../../connect/jdbc/reference/setarray-method-sqlserverpreparedstatement.md)|(から継承された[SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md))。指定された配列オブジェクトを指定されたパラメーターの数を設定します。|  
|[setAsciiStream](../../../connect/jdbc/reference/setasciistream-sqlservercallablestatement.md)|指定されたパラメーターを、渡された入力ストリームに設定します。|  
|[setBigDecimal](../../../connect/jdbc/reference/setbigdecimal-method-sqlservercallablestatement.md)|指定された BigDecimal オブジェクトに指定されたパラメーターを設定します。|  
|[setBinaryStream](../../../connect/jdbc/reference/setbinarystream-sqlservercallablestatement.md)|指定されたパラメーターを、指定された入力ストリームに設定します。|  
|[setBlob](../../../connect/jdbc/reference/setblob-method-sqlserverpreparedstatement.md)|(から継承された[SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md))。指定された Blob オブジェクトに指定されたパラメーターを設定します。|  
|[setboolean](../../../connect/jdbc/reference/setboolean-method-sqlservercallablestatement.md)|指定されたパラメーターを設定、指定された**ブール**値。|  
|[setByte](../../../connect/jdbc/reference/setbyte-method-sqlservercallablestatement.md)|指定されたパラメーターを設定して、指定された**バイト**値。|  
|[SetBytes](../../../connect/jdbc/reference/setbytes-method-sqlservercallablestatement.md)|指定した配列に指定されたパラメーターを設定**バイト**値。|  
|[setCharacterStream](../../../connect/jdbc/reference/setcharacterstream-method-sqlservercallablestatement.md)|指定されたリーダー オブジェクトを指定されたパラメーターを設定します。|  
|[setClob](../../../connect/jdbc/reference/setclob-method-sqlservercallablestatement.md)|(から継承された[SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md))。指定されたパラメーターを、指定されたオブジェクトに設定します。|  
|[setCursorName](../../../connect/jdbc/reference/setcursorname-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。SQL カーソル名を、渡された文字列に設定します。この文字列は、後に続く実行 (execute) メソッドによって使用されます。|  
|[setDate](../../../connect/jdbc/reference/setdate-method-sqlservercallablestatement.md)|指定されたパラメーターを、渡された日付の値に設定します。|  
|[setDateTimeOffset](../../../connect/jdbc/reference/setdatetimeoffset-method-sqlservercallablestatement.md)|指定された列の値を設定、 [DateTimeOffset クラス](../../../connect/jdbc/reference/datetimeoffset-class.md)値。|  
|[setDouble](../../../connect/jdbc/reference/setdouble-method-sqlservercallablestatement.md)|指定されたパラメーターを設定、指定された**二重**値。|  
|[setEscapeProcessing](../../../connect/jdbc/reference/setescapeprocessing-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。エスケープの処理モードを設定します。|  
|[setFetchDirection](../../../connect/jdbc/reference/setfetchdirection-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。結果セットの行を処理する方向についてのヒントを JDBC ドライバーに示します。|  
|[setFetchSize](../../../connect/jdbc/reference/setfetchsize-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。さらに行が必要な場合にデータベースからフェッチする必要がある行数について、JDBC ドライバーにヒントを示します。|  
|[setFloat](../../../connect/jdbc/reference/setfloat-method-sqlservercallablestatement.md)|指定されたパラメーターを指定した設定**float**値。|  
|[setInt](../../../connect/jdbc/reference/setint-method-sqlservercallablestatement.md)|指定されたパラメーターを指定した設定**int**値。|  
|[setLong](../../../connect/jdbc/reference/setlong-method-sqlservercallablestatement.md)|指定されたパラメーターを指定した設定**長い**値。|  
|[setMaxFieldSize](../../../connect/jdbc/reference/setmaxfieldsize-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。内のバイトの最大数の上限を設定、 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)文字またはバイナリ値を指定したバイト数を格納する列。|  
|[setMaxRows](../../../connect/jdbc/reference/setmaxrows-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。行の最大数の上限を設定する[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトは、指定した数に含めることができます。|  
|[setNCharacterStream](../../../connect/jdbc/reference/setncharacterstream-method-sqlservercallablestatement.md)|指定された Reader オブジェクトを指定されたパラメーターを設定します。|  
|[setNClob](../../../connect/jdbc/reference/setnclob-method-sqlservercallablestatement.md)|指定されたパラメーターを、指定されたオブジェクトに設定します。|  
|[setNString](../../../connect/jdbc/reference/setnstring-method-sqlservercallablestatement.md)|指定された String オブジェクトを指定されたパラメーターを設定します。|  
|[setNull](../../../connect/jdbc/reference/setnull-method-sqlservercallablestatement.md)|渡されたパラメーターの型で、指定されたパラメーターを null 値に設定します。|  
|[setObject](../../../connect/jdbc/reference/setobject-method-sqlservercallablestatement.md)|指定したオブジェクトを使用して、指定されたパラメーターの値を設定します。|  
|[setPoolable](../../../connect/jdbc/reference/setpoolable-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。ステートメントをプールすること、またはプールしないことを要求します。 既定では、SQLServerCallableStatement オブジェクトは作成時にプールします。|  
|[setQueryTimeout](../../../connect/jdbc/reference/setquerytimeout-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。ドライバーが CallableStatement オブジェクトの指定した秒数に実行を待つ秒数を設定します。|  
|[setRef](../../../connect/jdbc/reference/setref-method-sqlserverpreparedstatement.md)|(から継承された[SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md))。指定された参照オブジェクトを指定されたパラメーターを設定します。|  
|[setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)|(から継承された[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md))。応答のバッファリング モードを設定[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクト大文字と小文字を**文字列完全**または**アダプティブ**です。|  
|[setShort](../../../connect/jdbc/reference/setshort-method-sqlservercallablestatement.md)|指定されたパラメーターを指定した設定**短い**値。|  
|[SetString](../../../connect/jdbc/reference/setstring-method-sqlservercallablestatement.md)|指定されたパラメーターを指定し、Java に設定**文字列**値。|  
|[setSQLXML](../../../connect/jdbc/reference/setsqlxml-method-sqlservercallablestatement.md)|指定されたパラメーターを指定した設定**SQLXML**オブジェクト。|  
|[setTime](../../../connect/jdbc/reference/settime-method-sqlservercallablestatement.md)|指定されたパラメーターを、指定された時刻の値に設定します。|  
|[setTimestamp](../../../connect/jdbc/reference/settimestamp-method-sqlservercallablestatement.md)|指定されたパラメーターを、指定されたタイムスタンプ値に設定します。|  
|[setUnicodeStream](../../../connect/jdbc/reference/setunicodestream-method-sqlserverpreparedstatement.md)|(から継承された[SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md))。指定されたパラメーターの番号を、渡された入力ストリームに設定します。入力ストリームは、指定されたバイト数を持ちます。|  
|[setURL](../../../connect/jdbc/reference/seturl-method-sqlservercallablestatement.md)|指定されたパラメーターを、指定された URL 値に設定します。|  
|[unwrap](../../../connect/jdbc/reference/unwrap-method-sqlservercallablestatement.md)|アクセス許可を指定したインターフェイスを実装するオブジェクトを返します、 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]-特定のメソッドです。|  
|[wasNull](../../../connect/jdbc/reference/wasnull-method-sqlservercallablestatement.md)|最後に読み取られた OUT パラメーターが SQL NULL かどうかを取得します。|  
  
## <a name="inherited-methods"></a>継承されたメソッド  
  
|継承元のクラス|メソッド|  
|---------------------------|-------------|  
|com.microsoft.sqlserver.jdbc.SQLServerPreparedStatement|addBatch、clearBatch、clearParameters、close、execute、executeBatch、executeQuery、executeUpdate、getMetaData、getParameterMetaData、setArray、setAsciiStream、setBigDecimal、setBinaryStream、setBlob、setboolean、setByte、setBytes、setCharacterStream、setClob、setDate、setDouble、setFloat、setInt、setLong、setNull、setObject、setRef、setShort、setString、setTime、setTimestamp、setUnicodeStream、setURL|  
|com.microsoft.sqlserver.jdbc.SQLServerStatement|cancel、clearWarnings、execute、executeUpdate、getConnection、getFetchDirection、getFetchSize、getGeneratedKeys、getMaxFieldSize、getMaxRows、getMoreResults、getQueryTimeout、getResultSet、getResultSetConcurrency、getResultSetHoldability、getResultSetType、getUpdateCount、getWarnings、isPoolable、setCursorName、setEscapeProcessing、setFetchDirection、setFetchSize、setMaxFieldSize、setMaxRows、setPoolable、setQueryTimeout|  
|class java.lang.Object|clone、equals、finalize、getClass、hashCode、notify、notifyAll、toString、wait|  
|java.sql.PreparedStatement|addBatch、clearParameters、execute、executeQuery、executeUpdate、getMetaData、getParameterMetaData、getSQLXML、setArray、setAsciiStream、setBigDecimal、setBinaryStream、setBlob、setboolean、setByte、setBytes、setCharacterStream、setClob、setDate、setDate、setDouble、setFloat、setInt、setLong、setNull、setObject、setRef、setShort、setString、setSQLXML、setTime、setTimestamp、setUnicodeStream、setURL|  
|java.sql.Statement|addBatch、cancel、clearBatch、clearWarnings、close、execute、executeBatch、executeQuery、executeUpdate、getConnection、getFetchDirection、getFetchSize、getGeneratedKeys、getMaxFieldSize、getMaxRows、getMoreResults、getQueryTimeout、getResultSet、getResultSetConcurrency、getResultSetHoldability、getResultSetType、getUpdateCount、getWarnings、setCursorName、setEscapeProcessing、setFetchDirection、setFetchSize、setMaxFieldSize、setMaxRows、setQueryTimeout|  
|java.sql.Wrapper|isWrapperFor、unwrap|  
  
## <a name="see-also"></a>参照  
 [SQLServerCallableStatement クラス](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
