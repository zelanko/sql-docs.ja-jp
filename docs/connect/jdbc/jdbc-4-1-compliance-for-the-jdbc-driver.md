---
title: "JDBC 4.1 準拠、JDBC driver |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f087fd40-8451-478e-b465-43112c711515
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: cffe6569f7bac5308d49bb89f4fb4db259be445b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/21/2017

---
# <a name="jdbc-41-compliance-for-the-jdbc-driver"></a>JDBC Driver の JDBC 4.1 への準拠
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

    
> [!NOTE]  
>  Microsoft JDBC Driver 4.2 for SQL Server より前のバージョンのドライバーは、Java Database Connectivity API 4.0 仕様に準拠しています。 このセクションは、4.2 リリースより前のバージョンには適用されません。  
  
 Java Database Connectivity API 4.1 仕様は Microsoft JDBC Driver 4.2 for SQL Server によってサポートされ、以下の API メソッドが実装されています。  
  
 **SQLServerConnection クラス**  
  
|新しいメソッド|Description|JDBC ドライバーの実装|  
|----------------|-----------------|--------------------------------|  
|void abort(Executor executor)|SQL Server への開いている接続を終了します。|java.sql.Connection インターフェイスの説明に従って実装されています。 詳細についてを参照してください[java.sql.Connection](http://docs.oracle.com/javase/7/docs/api/java/sql/Connection.html)です。|  
|void setSchema(String schema)|現在の接続のスキーマを設定します。|SQL Server は、現在のセッションのスキーマの設定をサポートしていません。 このメソッドが呼び出された場合、ドライバーは警告を表示せずに、警告メッセージをログに記録します。 詳細についてを参照してください[java.sql.Connection](http://docs.oracle.com/javase/7/docs/api/java/sql/Connection.html)です。|  
|String getSchema()|現在の接続のスキーマ名を返します。|SQL Server は、現在の接続のスキーマの設定をサポートしていないので、ドライバーは代わりにユーザーの既定のスキーマを返します。 詳細についてを参照してください[java.sql.Connection](http://docs.oracle.com/javase/7/docs/api/java/sql/Connection.html)です。|  
  
 **SQLServerDatabaseMetaData クラス**  
  
|新しいメソッド|Description|JDBC ドライバーの実装|  
|----------------|-----------------|--------------------------------|  
|boolean generatedKeyAlwaysReturned()|生成されたキーの取得をドライバーがサポートしているので true を返します|Java.sql」の説明に従って実装されています。 DatabaseMetaData インターフェイスです。 詳細については、次を参照してください。 [java.sql.DatabaseMetaData](http://docs.oracle.com/javase/7/docs/api/java/sql/DatabaseMetaData.html)です。|  
|ResultSet getPseudoColumns(String catalog, String schemaPattern,String tableNamePattern,String columnNamePattern)|擬似/非表示の列の説明を取得します。|SQL Server には擬似列の正式な概念がないので、空の結果セットを返します。 詳細については、次を参照してください。 [java.sql.DatabaseMetaData](http://docs.oracle.com/javase/7/docs/api/java/sql/DatabaseMetaData.html)です。|  
  
 **SQLServerStatement クラス**  
  
|新しいメソッド|Description|JDBC ドライバーの実装|  
|----------------|-----------------|--------------------------------|  
|void closeOnCompletion()|すべての依存結果セットが閉じられたときに、このステートメントが閉じられることを指定します。|Java.sql.Statement インターフェイスの説明に従って実装されています。 詳細については、次を参照してください。 [java.sql.Statement](http://docs.oracle.com/javase/7/docs/api/java/sql/Statement.html)です。|  
|boolean isCloseOnCompletion()|すべての依存結果セットが閉じられたときに、このステートメントが閉じられるかどうかを示す値を返します。|Java.sql.Statement インターフェイスの説明に従って実装されています。 詳細については、次を参照してください。 [java.sql.Statement](http://docs.oracle.com/javase/7/docs/api/java/sql/Statement.html)です。|  
  
 Java Database Connectivity API 4.1 仕様は Microsoft JDBC Driver 4.2 for SQL Server によってサポートされ、以下の機能が実装されています。  
  
|新機能|Description|  
|-----------------|-----------------|  
|新しいエスケープ関数<br /><br /> 制限された戻り行エスケープ|部分的にサポートされています。<br /><br /> エスケープ構文: 制限\<行 >[オフセット < row_offset >](/sql-docs/docs/connect/jdbc/using-sql-escape-sequences)です。|  
  
 Java Database Connectivity API 4.1 仕様は Microsoft JDBC Driver 4.2 for SQL Server によってサポートされ、以下のようにデータ型がマッピングされています。  
  
|データ型マッピング|Description|  
|------------------------|-----------------|  
|PreparedStatement.setObject() と PreparedStatement.setNull() メソッドで、新しいデータ型マッピングがサポートされるようになりました。|1.Java から JDBC 型への新しいマッピング<br /><br /> (a) java.math.BigInteger から JDBC BIGINT へ<br /><br /> (b) java.util.Date および java.util.Calendar から JDBC TIMESTAMP へ<br /><br /> 2.新しいデータ型変換:<br /><br /> (a) java.math.BigInteger から CHAR、VARCHAR、LONGVARCHAR、BIGINT へ<br /><br /> (b) java.util.Date および java.util.Calendar から CHAR、VARCHAR、LONGVARCHAR、DATE, TIME、TIMESTAMP へ<br /><br /> 詳細については、JDBC 4.1 の仕様を参照してください。|  
  
  
