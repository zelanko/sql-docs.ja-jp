---
title: "SQLServerResultSet のメンバー |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2a438d5d-2d6a-46a0-a2ae-f35fbae4a472
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 16088d8260afdd23c89d4d583153193b894f8249
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlserverresultset-members"></a>SQLServerResultSet のメンバー
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  次の表に、によって公開されるメンバー、 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)クラスです。  
  
## <a name="constructors"></a>コンス トラクター  
 [なし] :  
  
## <a name="fields"></a>フィールド  
  
|名前|Description|  
|----------|-----------------|  
|[CONCUR_SS_OPTIMISTIC_CC](../../../connect/jdbc/reference/concur-ss-optimistic-cc-field-sqlserverresultset.md)|指定するため、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]読み取り/書き込み行ロックなしでオプティミスティック同時実行制御の種類。|  
|[CONCUR_SS_OPTIMISTIC_CCVAL](../../../connect/jdbc/reference/concur-ss-optimistic-ccval-field-sqlserverresultset.md)|指定するため、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]読み取り/書き込み行ロックなしでオプティミスティック同時実行制御の種類。|  
|[CONCUR_SS_SCROLL_LOCKS](../../../connect/jdbc/reference/concur-ss-scroll-locks-field-sqlserverresultset.md)|指定するため、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]読み取り/書き込み行ロックでオプティミスティック同時実行制御の種類。|  
|[TYPE_SS_DIRECT_FORWARD_ONLY](../../../connect/jdbc/reference/type-ss-direct-forward-only-field-sqlserverresultset.md)|指定するため、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]高速順方向専用、読み取り専用のカーソルの種類。|  
|[TYPE_SS_SCROLL_DYNAMIC](../../../connect/jdbc/reference/type-ss-scroll-dynamic-field-sqlserverresultset.md)|指定するため、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]動的カーソルの種類。|  
|[TYPE_SS_SCROLL_KEYSET](../../../connect/jdbc/reference/type-ss-scroll-keyset-field-sqlserverresultset.md)|指定するため、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]キーセット カーソルの種類。|  
|[TYPE_SS_SCROLL_STATIC](../../../connect/jdbc/reference/type-ss-scroll-static-field-sqlserverresultset.md)|指定するため、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]静的カーソルの種類。|  
|[TYPE_SS_SERVER_CURSOR_FORWARD_ONLY](../../../connect/jdbc/reference/type-ss-server-cursor-forward-only-field-sqlserverresultset.md)|指定するため、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]高速順方向専用、読み取り専用のカーソルの種類。|  
  
## <a name="inherited-fields"></a>継承されたフィールド  
  
|継承元のクラス|Description|  
|---------------------------|-----------------|  
|java.sql.ResultSet|CLOSE_CURSORS_AT_COMMIT、CONCUR_READ_ONLY、CONCUR_UPDATABLE、FETCH_FORWARD、FETCH_REVERSE、FETCH_UNKNOWN、HOLD_CURSORS_OVER_COMMIT、TYPE_FORWARD_ONLY、TYPE_SCROLL_INSENSITIVE、TYPE_SCROLL_SENSITIVE|  
  
## <a name="methods"></a>メソッド  
  
|名前|Description|  
|----------|-----------------|  
|[絶対](../../../connect/jdbc/reference/absolute-method-sqlserverresultset.md)|これで、指定された行にカーソルを移動[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。|  
|[afterLast](../../../connect/jdbc/reference/afterlast-method-sqlserverresultset.md)|この最後の行の後にカーソルを移動[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。|  
|[beforeFirst](../../../connect/jdbc/reference/beforefirst-method-sqlserverresultset.md)|この最初の行の前にカーソルを移動[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。|  
|[cancelRowUpdates](../../../connect/jdbc/reference/cancelrowupdates-method-sqlserverresultset.md)|これで、現在の行に加えられた更新を取り消します[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。|  
|[clearWarnings](../../../connect/jdbc/reference/clearwarnings-method-sqlserverresultset.md)|これで報告されるすべての警告をクリア[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。|  
|[閉じる](../../../connect/jdbc/reference/close-method-sqlserverresultset.md)|このリリース[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトのデータベースと JDBC リソースを待たずにすぐに自動的に閉じられているときにします。|  
|[deleteRow](../../../connect/jdbc/reference/deleterow-method-sqlserverresultset.md)|これから現在の行を削除[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトと基になるデータベースからです。|  
|[最終処理します。](../../../connect/jdbc/reference/finalize-method-sqlserverresultset.md)|これを明示的に閉じる[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。|  
|[findColumn](../../../connect/jdbc/reference/findcolumn-method-sqlserverresultset.md)|これで指定された列名の最初の一致する列のインデックスを取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。|  
|[まずは](../../../connect/jdbc/reference/first-method-sqlserverresultset.md)|この最初の行にカーソルを移動[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。|  
|[getArray](../../../connect/jdbc/reference/getarray-method-sqlserverresultset.md)|この現在の行に指定された列の値を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトの配列オブジェクトとして。|  
|[getAsciiStream](../../../connect/jdbc/reference/getasciistream-method-sqlserverresultset.md)|この現在の行に指定された列の値を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) ASCII 文字のストリームとしてオブジェクト。|  
|[getBigDecimal](../../../connect/jdbc/reference/getbigdecimal-method-sqlserverresultset.md)|この現在の行に指定された列インデックスの値を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) java.math.BigDecimal としてオブジェクト。|  
|[getBinaryStream](../../../connect/jdbc/reference/getbinarystream-method-sqlserverresultset.md)|この現在の行に指定された列の値を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトとして解釈されないバイトのバイナリ ストリーム。|  
|[getBlob](../../../connect/jdbc/reference/getblob-method-sqlserverresultset.md)|この現在の行に指定された列の値を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトを Java プログラミング言語での Blob オブジェクトとして。|  
|[getBoolean](../../../connect/jdbc/reference/getboolean-method-sqlserverresultset.md)|この現在の行に指定された列の値を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトとして、**ブール**Java プログラミング言語でします。|  
|[getByte](../../../connect/jdbc/reference/getbyte-method-sqlserverresultset.md)|この現在の行に指定された列の値を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトとして、**バイト**Java プログラミング言語でします。|  
|[getBytes](../../../connect/jdbc/reference/getbytes-method-sqlserverresultset.md)|この現在の行に指定された列の値を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトとして、**バイト**Java プログラミング言語の配列。|  
|[getCharacterStream](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverresultset.md)|この現在の行に指定された列の値を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトを java.io.Reader オブジェクトとして。|  
|[getClob](../../../connect/jdbc/reference/getclob-method-sqlserverresultset.md)|この現在の行に指定された列の値を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトを Java プログラミング言語で Clob オブジェクトとして。|  
|[getConcurrency](../../../connect/jdbc/reference/getconcurrency-method-sqlserverresultset.md)|この同時実行モードを取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。|  
|[getCursorName](../../../connect/jdbc/reference/getcursorname-method-sqlserverresultset.md)|これによって使用される SQL カーソルの名前を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。|  
|[getDate](../../../connect/jdbc/reference/getdate-method-sqlserverresultset.md)|この現在の行に指定された列の値を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトを Java プログラミング言語の java.sql.Date オブジェクトとして。|  
|[getDateTimeOffset](../../../connect/jdbc/reference/getdatetimeoffset-sqlserverresultset.md)|指定した列の値を取得、[DateTimeOffset クラス](../../../connect/jdbc/reference/datetimeoffset-class.md)オブジェクト。|  
|[getDouble](../../../connect/jdbc/reference/getdouble-method-sqlserverresultset.md)|この現在の行に指定された列の値を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトとして、**二重**Java プログラミング言語でします。|  
|[getFetchDirection](../../../connect/jdbc/reference/getfetchdirection-method-sqlserverresultset.md)|このフェッチ方向を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。|  
|[getFetchSize](../../../connect/jdbc/reference/getfetchsize-method-sqlserverresultset.md)|このため、フェッチ サイズを取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。|  
|[getFloat](../../../connect/jdbc/reference/getfloat-method-sqlserverresultset.md)|この現在の行に指定された列の値を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトとして、 **float** Java プログラミング言語でします。|  
|[getHoldability](../../../connect/jdbc/reference/getholdability-method-sqlserverresultset.md)|これの保持機能を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。|  
|[getInt](../../../connect/jdbc/reference/getint-method-sqlserverresultset.md)|この現在の行に指定された列の値を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトとして、 **int** Java プログラミング言語でします。|  
|[getLong](../../../connect/jdbc/reference/getlong-method-sqlserverresultset.md)|この現在の行に指定された列の値を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトとして、**長い**Java プログラミング言語でします。|  
|[getMetaData](../../../connect/jdbc/reference/getmetadata-method-sqlserverresultset.md)|数、型、およびこれのプロパティを取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトの列です。|  
|[getNCharacterStream](../../../connect/jdbc/reference/getncharacterstream-method-sqlserverresultset.md)|現在の行に指定された列の値を取得、 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)リーダー オブジェクトとしてオブジェクト。|  
|[getNClob](../../../connect/jdbc/reference/getnclob-method-sqlserverresultset.md)|現在の行に指定された列の値を取得、 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトとして、 **NClob** Java プログラミング言語のオブジェクト。|  
|[getNString](../../../connect/jdbc/reference/getnstring-method-sqlserverresultset.md)|現在の行に指定された列の値を取得、 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) java プログラミング言語の string オブジェクト。|  
|[getObject](../../../connect/jdbc/reference/getobject-method-sqlserverresultset.md)|この現在の行に指定された列の値を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) Java プログラミング言語でオブジェクトとして。|  
|[getRef](../../../connect/jdbc/reference/getref-method-sqlserverresultset.md)|この現在の行に指定された列の値を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトを Java プログラミング言語で Ref オブジェクトとして。|  
|[getRow](../../../connect/jdbc/reference/getrow-method-sqlserverresultset.md)|現在の行番号を取得します。|  
|[getShort](../../../connect/jdbc/reference/getshort-method-sqlserverresultset.md)|この現在の行に指定された列の値を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトとして、**短い**Java プログラミング言語でします。|  
|[getStatement](../../../connect/jdbc/reference/getstatement-method-sqlserverresultset.md)|取得、 [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)をこれを生成したオブジェクト[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。|  
|[getString](../../../connect/jdbc/reference/getstring-method-sqlserverresultset.md)|この現在の行に指定された列の値を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトとして、**文字列**Java プログラミング言語でします。|  
|[getSQLXML](../../../connect/jdbc/reference/getsqlxml-method-sqlserverresultset.md)|現在の行に指定された列の値を取得、 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトとして、 **SQLXML**オブジェクト。|  
|[getTime](../../../connect/jdbc/reference/gettime-method-sqlserverresultset.md)|この現在の行に指定された列の値を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトを Java プログラミング言語の java.sql.Time オブジェクトとして。|  
|[getTimestamp](../../../connect/jdbc/reference/gettimestamp-method-sqlserverresultset.md)|この現在の行に指定された列の値を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトを Java プログラミング言語の java.sql.Timestamp オブジェクトとして。|  
|[getType](../../../connect/jdbc/reference/gettype-method-sqlserverresultset.md)|このカーソルの種類を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。|  
|[getUnicodeStream](../../../connect/jdbc/reference/getunicodestream-method-sqlserverresultset.md)|この現在の行に指定された列の値を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) Unicode 文字のストリームとしてオブジェクト。|  
|[getURL](../../../connect/jdbc/reference/geturl-method-sqlserverresultset.md)|この現在の行に指定された列の値を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) URL オブジェクトとしてオブジェクト。|  
|[getWarnings](../../../connect/jdbc/reference/getwarnings-method-sqlserverresultset.md)|この呼び出しによって報告された最初の警告取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。|  
|[insertRow](../../../connect/jdbc/reference/insertrow-method-sqlserverresultset.md)|これに挿入行の内容を挿入[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトとデータベースにします。|  
|[isAfterLast](../../../connect/jdbc/reference/isafterlast-method-sqlserverresultset.md)|この最後の行の後ろにカーソルがあるかどうかを取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。|  
|[isBeforeFirst](../../../connect/jdbc/reference/isbeforefirst-method-sqlserverresultset.md)|この最初の行の前にカーソルがあるかどうかを取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。|  
|[isClosed](../../../connect/jdbc/reference/isclosed-method-sqlserverresultset.md)|示すかどうかこの[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトが閉じられました。|  
|[isFirst](../../../connect/jdbc/reference/isfirst-method-sqlserverresultset.md)|この最初の行の上にカーソルがあるかどうかを取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。|  
|[isLast](../../../connect/jdbc/reference/islast-method-sqlserverresultset.md)|上のこの最後の行にカーソルがあるかどうかを取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。|  
|[前の](../../../connect/jdbc/reference/last-method-sqlserverresultset.md)|この最後の行にカーソルを移動[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。|  
|[moveToCurrentRow](../../../connect/jdbc/reference/movetocurrentrow-method-sqlserverresultset.md)|記憶されているカーソルの位置に、現在の行では通常、カーソルを移動します。|  
|[moveToInsertRow](../../../connect/jdbc/reference/movetoinsertrow-method-sqlserverresultset.md)|カーソルを挿入行に移動します。|  
|[次に](../../../connect/jdbc/reference/next-method-sqlserverresultset.md)|カーソルを現在の位置から 1 行下に移動します。|  
|[先の](../../../connect/jdbc/reference/previous-method-sqlserverresultset.md)|この前の行にカーソルを移動[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。|  
|[refreshRow](../../../connect/jdbc/reference/refreshrow-method-sqlserverresultset.md)|データベース内の最新の値を使用して、現在の行を更新します。|  
|[相対](../../../connect/jdbc/reference/relative-method-sqlserverresultset.md)|正または負の値の方向のいずれかで、現在の行を基準とした、行の特定の量、カーソルを移動します。|  
|[rowDeleted](../../../connect/jdbc/reference/rowdeleted-method-sqlserverresultset.md)|行が削除されたかどうかを取得します。|  
|[rowInserted](../../../connect/jdbc/reference/rowinserted-method-sqlserverresultset.md)|現在の行に挿入があったかどうかを取得します。|  
|[rowUpdated](../../../connect/jdbc/reference/rowupdated-method-sqlserverresultset.md)|現在の行が更新されたかどうかを取得します。|  
|[setFetchDirection](../../../connect/jdbc/reference/setfetchdirection-method-sqlserverresultset.md)|方向についてのヒントは、この行[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトが処理されます。|  
|[setFetchSize](../../../connect/jdbc/reference/setfetchsize-method-sqlserverresultset.md)|複数の行は、この必要な場合に、データベースからフェッチする必要があります行の数についてのヒントを JDBC ドライバーに提供[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。|  
|[updateArray](../../../connect/jdbc/reference/updatearray-method-sqlserverresultset.md)|配列オブジェクトで指定された列を更新します。|  
|[updateAsciiStream](../../../connect/jdbc/reference/updateasciistream-method-sqlserverresultset.md)|指定された列を ASCII ストリーム値で更新します。|  
|[updateBigDecimal](../../../connect/jdbc/reference/updatebigdecimal-method-sqlserverresultset.md)|BigDecimal オブジェクトで指定された列を更新します。|  
|[updateBinaryStream](../../../connect/jdbc/reference/updatebinarystream-method-sqlserverresultset.md)|指定された列をバイナリ ストリーム値で更新します。|  
|[updateBlob](../../../connect/jdbc/reference/updateblob-method-sqlserverresultset.md)|指定された列を java.sql.Blob 値で更新します。|  
|[updateBoolean](../../../connect/jdbc/reference/updateboolean-method-sqlserverresultset.md)|指定された列の更新、**ブール**値。|  
|[updateByte](../../../connect/jdbc/reference/updatebyte-method-sqlserverresultset.md)|指定された列の更新、**バイト**値。|  
|[updateBytes](../../../connect/jdbc/reference/updatebytes-method-sqlserverresultset.md)|配列で指定された列を更新**バイト**値。|  
|[updateCharacterStream](../../../connect/jdbc/reference/updatecharacterstream-method-sqlserverresultset.md)|指定された列を文字ストリームの値で更新します。|  
|[updateClob](../../../connect/jdbc/reference/updateclob-method-sqlserverresultset.md)|指定された列を java.sql.Clob 値で更新します。|  
|[updateDate](../../../connect/jdbc/reference/updatedate-method-sqlserverresultset.md)|指定された列を日付の値で更新します。|  
|[updateDateTimeOffset](../../../connect/jdbc/reference/updatedatetimeoffset-sqlserverresultset.md)|更新プログラム、 [DateTimeOffset クラス](../../../connect/jdbc/reference/datetimeoffset-class.md)列です。|  
|[updateDouble](../../../connect/jdbc/reference/updatedouble-method-sqlserverresultset.md)|指定された列の更新、**二重**値。|  
|[updateFloat](../../../connect/jdbc/reference/updatefloat-method-sqlserverresultset.md)|指定された列の更新、 **float**値。|  
|[updateInt](../../../connect/jdbc/reference/updateint-method-sqlserverresultset.md)|指定された列の更新、 **int**値。|  
|[updateLong](../../../connect/jdbc/reference/updatelong-method-sqlserverresultset.md)|指定された列の更新、**長い**値。|  
|[updateNCharacterStream](../../../connect/jdbc/reference/updatencharacterstream-method-sqlserverresultset.md)|指定された列を文字ストリームの値で更新します。|  
|[updateNClob](../../../connect/jdbc/reference/updatenclob-method-sqlserverresultset.md)|指定された列を指定されたオブジェクト値で更新します。|  
|[updateNString](../../../connect/jdbc/reference/updatenstring-method-sqlserverresultset.md)|指定された列の更新、**文字列**値。|  
|[updateNull](../../../connect/jdbc/reference/updatenull-method-sqlserverresultset.md)|指定された列を null 値で更新します。|  
|[updateObject](../../../connect/jdbc/reference/updateobject-method-sqlserverresultset.md)|指定された列の更新、**オブジェクト**値。|  
|[updateRef](../../../connect/jdbc/reference/updateref-method-sqlserverresultset.md)|指定された列を java.sql.Ref 値で更新します。|  
|[updateRow](../../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md)|この現在の行の新しい内容で基になるデータベースを更新[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。|  
|[updateShort](../../../connect/jdbc/reference/updateshort-method-sqlserverresultset.md)|指定された列の更新、**短い**値。|  
|[updateString](../../../connect/jdbc/reference/updatestring-method-sqlserverresultset.md)|指定された列の更新、**文字列**値。|  
|[updateSQLXML](../../../connect/jdbc/reference/updatesqlxml-method-sqlserverresultset.md)|指定された列の更新、 **SQLXML**値。|  
|[updateTime](../../../connect/jdbc/reference/updatetime-method-sqlserverresultset.md)|指定された列を時刻の値で更新します。|  
|[updateTimestamp](../../../connect/jdbc/reference/updatetimestamp-method-sqlserverresultset.md)|指定された列をタイムスタンプ値で更新します。|  
|[wasNull](../../../connect/jdbc/reference/wasnull-method-sqlserverresultset.md)|最後に読み取られた値が null 値にされたかどうかを確認します。|  
  
## <a name="inherited-methods"></a>継承されたメソッド  
  
|継承元のクラス|メソッド|  
|---------------------------|-------------|  
|java.lang.Object|clone、equals、getClass、hashCode、notify、notifyAll、toString、wait|  
|java.sql.Wrapper|isWrapperFor、unwrap|  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

