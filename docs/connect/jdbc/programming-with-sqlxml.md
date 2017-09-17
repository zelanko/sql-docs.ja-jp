---
title: "SQLXML でのプログラミング |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4d2cc57c-7293-4d92-b8b1-525e2b35f591
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5737ae7a0356f7697b254e67faa5cf715d2ffaef
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="programming-with-sqlxml"></a>SQLXML でのプログラミング
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  このセクションを使用する方法について説明、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]格納および XML を取得する API メソッドにドキュメント化にリレーショナル データベースから**SQLXML**オブジェクト。  
  
 また、このセクションでは、SQLXML オブジェクトの種類に関する情報を格納し、SQLXML オブジェクトを使用する場合は、重要なガイドラインと制限事項の一覧を示します。  
  
## <a name="reading-and-writing-xml-data-with-sqlxml-objects"></a>SQLXML オブジェクトを使用した XML データの読み取りと書き込み  
 次のリストを使用する方法を説明する、 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] API のメソッドと SQLXML オブジェクトの XML データを読み書きします。  
  
-   SQLXML オブジェクトを作成するを使用して、 [createSQLXML](../../connect/jdbc/reference/createsqlxml-method-sqlserverconnection.md)のメソッド、 [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)クラスです。 このメソッドで作成される SQLXML オブジェクトにはデータが一切含まれていないことに注意してください。 追加する**xml** SQLXML オブジェクトにデータを呼び出し、SQLXML インターフェイスに指定されている次のいずれかの: setResult、setCharacterStream、setBinaryStream、または setString です。  
  
-   SQLXML オブジェクトそのものを取得するには、getSQLXML メソッドを使用して、 [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)クラスまたは[SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)クラスです。  
  
-   取得する、 **xml** SQLXML オブジェクトからデータを使用して、SQLXML インターフェイスに指定されている次のいずれかの: getSource、getCharacterStream、getBinaryStream、または getString です。  
  
-   更新する、 **xml** SQLXML オブジェクト内のデータを使用して、 [updateSQLXML](../../connect/jdbc/reference/updatesqlxml-method-sqlserverresultset.md)のメソッド、 [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)クラスです。  
  
-   SQLXML オブジェクトの種類のデータベース テーブルの列に格納する**xml**の setSQLXML メソッドを使用して、 [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)クラスまたは[SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)クラスです。  
  
 コード例[SQLXML データ型のサンプル](../../connect/jdbc/sqlxml-data-type-sample.md)API の一般的なタスクを実行する方法を示します。  
  
## <a name="readable-and-writable-sqlxml-objects"></a>読み取り/書き込み可能な SQLXML オブジェクト  
 次の表は、JDBC API の setter、getter、および updater メソッドによってサポートされる SQLXML オブジェクトの種類を一覧にしたものです。 この表の各列の意味は次のとおりです。  
  
-   **メソッド名**列には、JDBC API でサポートされている getter、setter、および updater メソッドが一覧表示します。  
  
-   **Getter SQLXML オブジェクト**列は、いずれかで作成される SQLXML オブジェクトを表す、 [getSQLXML](../../connect/jdbc/reference/getsqlxml-method-sqlservercallablestatement.md)のメソッド、 [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)クラスや、 [getSQLXML](../../connect/jdbc/reference/getsqlxml-method-sqlserverresultset.md)のメソッド、 [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)クラスです。  
  
-   **Setter SQLXML オブジェクト**列によって作成される SQLXML オブジェクトを表します、 [createSQLXML](../../connect/jdbc/reference/createsqlxml-method-sqlserverconnection.md)のメソッド、 [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)クラスです。 以下の setter メソッドがによって作成された SQLXML オブジェクトのみを受け入れることに注意してください、 [createSQLXML](../../connect/jdbc/reference/createsqlxml-method-sqlserverconnection.md)メソッドです。  
  
|メソッド名|getter SQLXML オブジェクト<br /><br /> (読み取り可能)|setter SQLXML オブジェクト<br /><br /> (書き込み可能)|  
|-----------------|-------------------------------------------|-------------------------------------------|  
|CallableStatement.setSQLXML()|サポートされていません|Supported|  
|CallableStatement.setObject()|サポートされていません|Supported|  
|PreparedStatement.setSQLXML()|サポートされていません|Supported|  
|PreparedStatement.setObject()|サポートされていません|Supported|  
|ResultSet.updateSQLXML()|サポートされていません|Supported|  
|ResultSet.updateObject()|サポートされていません|Supported|  
|ResultSet.getSQLXML()|Supported|サポートされていません|  
|CallableStatement.getSQLXML()|Supported|サポートされていません|  
  
 この表を見るとわかるように、setter SQLXML メソッドは、読み取り可能な SQLXML オブジェクトでは使用できません。同様に、getter メソッドを書き込み可能な SQLXML オブジェクトで使用することもできません。  
  
 アプリケーションでは、SQLXML オブジェクトを小数点以下桁数または長さのパラメーターを指定して setObject メソッドを呼び出し、小数点以下桁数または長さのパラメーターは無視されます。  
  
## <a name="guidelines-and-limitations-when-using-sqlxml-objects"></a>SQLXML オブジェクトを使用する場合のガイドラインと制限  
 アプリケーションは SQLXML オブジェクトを使用して、データベースとの間で XML データの読み取りと書き込みを行うことができます。 以下に、SQLXML オブジェクトを使用するうえでの特定の制限と指針を箇条書きでまとめました。  
  
-   SQLXML オブジェクトの有効期間は、そのオブジェクトが作成されたトランザクションの期間内に限られます。  
  
-   getter メソッドから受け取った SQLXML オブジェクトは、データの読み取りにしか使用できません。  
  
-   接続オブジェクトによって作成された SQLXML オブジェクトは、データの書き込みにしか使用できません。  
  
-   アプリケーションは、読み取り可能な SQLXML オブジェクトの getter メソッドを 1 つだけ呼び出してデータを読み取ることができます。 getter メソッドを呼び出した後で、同じ SQLXML オブジェクトの他の getter メソッドまたは setter メソッドを呼び出そうとするとエラーになります。  
  
-   読み取りやに書き込まれた後、アプリケーションは SQLXML オブジェクトの free メソッドのみを呼び出すことができます。 ただし、基になる列またはパラメーターが有効である限り、返されたストリームまたはソースを処理することは可能です。 基になる列またはパラメーターが無効になった場合、SQLXML オブジェクトに関連付けられていたストリームやソースは閉じられます。 基になる列またはパラメーターが無効になった時点で、ストリーム、SAX (Simple API for XML)、および StAX (Streaming API for XML) の getter の基となっているデータが利用できなくなります。  
  
-   アプリケーションは、書き込み可能な SQLXML オブジェクトの setter メソッドを 1 つだけ呼び出すことができます。 setter メソッドを呼び出した後で、同じ SQLXML オブジェクトの他の setter メソッドまたは getter メソッドを呼び出そうとするとエラーになります。  
  
-   SQLXML オブジェクトに対してデータを設定するには、返されたオブジェクトの適切な setter メソッドや関数を使用する必要があります。  
  
-   GetSQLXML メソッド、 [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)クラスおよび[SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)クラスを返します**null**データの場合は、基になる列が**null**です。  
  
-   setter オブジェクトは、そのオブジェクトが作成された接続の間、有効です。  
  
-   アプリケーションを設定することはできません、 **null** SQLXML インターフェイスによって提供される set アクセス操作子メソッドを使用した値です。 アプリケーションから、SQLXML インターフェイスに定義されている setter メソッドを使用して空の文字列 ("") を設定することはできます。 設定する、 **null**値アプリケーション呼び出す必要があります、次のいずれか。  
  
    -   SetNull メソッド、 [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)クラスと[SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)クラスです。  
  
    -   SetObject メソッド、 [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)クラスと[SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)クラスです。  
  
    -   SetSQLXML メソッド、 [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)クラスと[SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)クラス、 **null**パラメーターの値。  
  
-   XML ドキュメントを扱う場合は、パフォーマンス上の理由から、Document Object Model (DOM) パーサーではなく、Simple API for XML (SAX) および Streaming API for XML (StAX) パーサーの使用をお勧めします。  
  
 XML パーサーは空の値を処理できません。 ただし、SQL Server が介在することで、アプリケーションが、XML データ型のデータベース列から空の値を取得したり、空の値を格納したりできるようになっています。 つまり、XML データを解析する際、基になる値が空である場合は、パーサーによって例外がスローされます。 DOM 出力の場合、JDBC ドライバーがその例外をキャッチして、エラーをスローします。 SAX および Stax 出力の場合、エラーは直接パーサーから送られます。  
  
## <a name="adaptive-buffering-and-sqlxml-support"></a>アダプティブ バッファリングと SQLXML サポート  
 SQLXML オブジェクトから返されたバイナリ ストリームと文字ストリームは、アダプティブ バッファリング モードまたはフル バッファリング モードに従います。 一方、XML パーサーがストリームではない場合、アダプティブとフルのいずれの設定にも従いません。 アダプティブ バッファリングの詳細については、次を参照してください。[アダプティブ バッファリングを使用して](../../connect/jdbc/using-adaptive-buffering.md)です。  
  
## <a name="see-also"></a>参照  
 [XML データのサポート](../../connect/jdbc/supporting-xml-data.md)  
  
  
