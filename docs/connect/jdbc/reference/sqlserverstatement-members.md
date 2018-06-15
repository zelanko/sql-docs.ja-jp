---
title: SQLServerStatement のメンバー |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 828cbaa9-ea7a-4986-95c3-5ba0d7d01d83
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 77161ec9693615eb50d4e62fb9cd1f6f185d23fe
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32853027"
---
# <a name="sqlserverstatement-members"></a>SQLServerStatement のメンバー
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  次の表に、によって公開されるメンバー、 [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)クラスです。  
  
## <a name="constructors"></a>コンス トラクター  
 [なし] :  
  
## <a name="fields"></a>フィールド  
 [なし] :  
  
## <a name="inherited-fields"></a>継承されたフィールド  
  
|名前|Description|  
|----------|-----------------|  
|java.sql.Statement|CLOSE_ALL_RESULTS、CLOSE_CURRENT_RESULT、EXECUTE_FAILED、KEEP_CURRENT_RESULT、NO_GENERATED_KEYS、RETURN_GENERATED_KEYS、SUCCESS_NO_INFO|  
  
## <a name="methods"></a>メソッド  
  
|名前|Description|  
|----------|-----------------|  
|[addBatch](../../../connect/jdbc/reference/addbatch-method-sqlserverstatement.md)|このコマンドの現在のリストに渡された SQL コマンドを追加[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクト。|  
|[cancel](../../../connect/jdbc/reference/cancel-method-sqlserverstatement.md)|これによって現在実行されている SQL ステートメントを取り消します[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクト。|  
|[clearBatch](../../../connect/jdbc/reference/clearbatch-method-sqlserverstatement.md)|[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) オブジェクトに対する SQL コマンドの現在の一覧を空にします。|  
|[clearWarnings](../../../connect/jdbc/reference/clearwarnings-method-sqlserverstatement.md)|これで報告されたすべての警告をクリア[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクト。|  
|[close](../../../connect/jdbc/reference/close-method-sqlserverstatement.md)|このリリース[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクトのデータベースと JDBC リソースを待たずにすぐに自動的に解放します。|  
|[execute](../../../connect/jdbc/reference/execute-method-sqlserverstatement.md)|渡された SQL ステートメントを実行します。このステートメントは、複数の結果を返す場合があります。|  
|[executeBatch](../../../connect/jdbc/reference/executebatch-method-sqlserverstatement.md)|実行するコマンド バッチをデータベースに送信します。 すべてのコマンドが正常に実行されている場合は、更新数の配列が返されます。|  
|[さらに executeQuery](../../../connect/jdbc/reference/executequery-method-sqlserverstatement.md)|渡された SQL ステートメントを実行し、1 つの [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) オブジェクトを返します。|  
|[executeUpdate](../../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md)|渡された SQL ステートメントを実行します。ステートメントは INSERT、UPDATE、MERGE、DELETE、または SQL DDL ステートメントのような何も返さない SQL ステートメントが可能です。|  
|[getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverstatement.md)|取得、 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)をこれを生成したオブジェクト[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクト。|  
|[getFetchDirection](../../../connect/jdbc/reference/getfetchdirection-method-sqlserverstatement.md)|これから生成された結果セットの既定値は、データベース テーブルから行をフェッチの方向を取得[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクト。|  
|[getFetchSize](../../../connect/jdbc/reference/getfetchsize-method-sqlserverstatement.md)|結果の数のセットの結果セットから生成されたオブジェクトの既定のフェッチ サイズである行を取得[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクト。|  
|[getGeneratedKeys](../../../connect/jdbc/reference/getgeneratedkeys-method-sqlserverstatement.md)|これを実行した結果作成される自動生成キー取得[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクト。|  
|[getMaxFieldSize](../../../connect/jdbc/reference/getmaxfieldsize-method-sqlserverstatement.md)|文字やバイナリ列の値に返されるバイトの最大数を取得、 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)これによって生成されるオブジェクト[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクト。|  
|[getMaxRows](../../../connect/jdbc/reference/getmaxrows-method-sqlserverstatement.md)|行の最大数を取得する、 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)これによって生成されるオブジェクト[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクトを含めることができます。|  
|[getMoreResults](../../../connect/jdbc/reference/getmoreresults-method-sqlserverstatement.md)|この次の結果に移動[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクト。|  
|[getQueryTimeout](../../../connect/jdbc/reference/getquerytimeout-method-sqlserverstatement.md)|秒数を取得、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]が待つこの[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクトを実行します。|  
|[getResponseBuffering](../../../connect/jdbc/reference/getresponsebuffering-method-sqlserverstatement.md)|応答のバッファリング モードを取得[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクト。|  
|[getResultSet](../../../connect/jdbc/reference/getresultset-method-sqlserverstatement.md)|現在の結果として取得、 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。|  
|[getResultSetConcurrency](../../../connect/jdbc/reference/getresultsetconcurrency-method-sqlserverstatement.md)|結果セットの同時実行を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)これによって生成されたオブジェクトの[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクト。|  
|[getResultSetHoldability](../../../connect/jdbc/reference/getresultsetholdability-method-sqlserverstatement.md)|結果セットの保持機能を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)これによって生成されたオブジェクトの[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクト。|  
|[getResultSetType](../../../connect/jdbc/reference/getresultsettype-method-sqlserverstatement.md)|結果セットの種類の取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)これによって生成されたオブジェクトの[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクト。|  
|[getUpdateCount](../../../connect/jdbc/reference/getupdatecount-method-sqlserverstatement.md)|現在の結果を更新数として取得します。|  
|[getWarnings](../../../connect/jdbc/reference/getwarnings-method-sqlserverstatement.md)|この呼び出しによって報告された最初の警告取得[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクト。|  
|[isClosed](../../../connect/jdbc/reference/isclosed-method-sqlserverstatement.md)|示すかどうかこの[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクトが閉じられました。|  
|[isPoolable](../../../connect/jdbc/reference/ispoolable-method-sqlserverstatement.md)|ユーザー指定のステートメント プールにステートメントを追加できるかどうかを示す値を返します。|  
|[isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverstatement.md)|ステートメント オブジェクトが指定されたインターフェイスのラッパーであるかどうかを示します。|  
|[setCursorName](../../../connect/jdbc/reference/setcursorname-method-sqlserverstatement.md)|SQL カーソル名を、渡された文字列に設定します。この文字列は、後に続く実行 (execute) メソッドによって使用されます。|  
|[setEscapeProcessing](../../../connect/jdbc/reference/setescapeprocessing-method-sqlserverstatement.md)|エスケープの処理モードを設定します。|  
|[setFetchDirection](../../../connect/jdbc/reference/setfetchdirection-method-sqlserverstatement.md)|結果セットの行を処理する方向についてのヒントを JDBC ドライバーに示します。|  
|[setFetchSize](../../../connect/jdbc/reference/setfetchsize-method-sqlserverstatement.md)|さらに行が必要な場合にデータベースからフェッチする必要がある行数について、JDBC ドライバーにヒントを示します。|  
|[setMaxFieldSize](../../../connect/jdbc/reference/setmaxfieldsize-method-sqlserverstatement.md)|内のバイトの最大数の上限を設定、 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)文字またはバイナリ値を指定したバイト数を格納する列。|  
|[setMaxRows](../../../connect/jdbc/reference/setmaxrows-method-sqlserverstatement.md)|行の最大数の上限を設定する[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトは、指定した数値を含めることができます。|  
|[setPoolable](../../../connect/jdbc/reference/setpoolable-method-sqlserverstatement.md)|ステートメントをプールすること、またはプールしないことを要求します。|  
|[setQueryTimeout](../../../connect/jdbc/reference/setquerytimeout-method-sqlserverstatement.md)|ドライバーが待つ秒数を設定、 [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクトを指定した秒数を実行します。|  
|[setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)|応答のバッファリング モードを設定[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクト大文字と小文字を**文字列完全**または**アダプティブ**です。|  
|[unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md)|アクセス許可を指定したインターフェイスを実装するオブジェクトを返します、 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]-特定のメソッドです。|  
  
## <a name="inherited-methods"></a>継承されたメソッド  
  
|継承元のクラス|メソッド|  
|---------------------------|-------------|  
|java.lang.Object|clone、equals、getClass、hashCode、notify、notifyAll、toString、wait|  
|java.sql.Wrapper|isWrapperFor、unwrap|  
  
## <a name="see-also"></a>参照  
 [SQLServerStatement クラス](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
