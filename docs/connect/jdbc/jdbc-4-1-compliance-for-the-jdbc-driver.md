---
title: JDBC 4.1 準拠、JDBC ドライバーの |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: f087fd40-8451-478e-b465-43112c711515
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e5cdf9c694323c345525752c733afc6a49482ac0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47722880"
---
# <a name="jdbc-41-compliance-for-the-jdbc-driver"></a>JDBC Driver の JDBC 4.1 への準拠
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

    
> [!NOTE]  
>  Microsoft JDBC Driver 4.2 for SQL Server より前のバージョンのドライバーは、Java Database Connectivity API 4.0 仕様に準拠しています。 このセクションは、4.2 リリースより前のバージョンには適用されません。  
  
 Java Database Connectivity API 4.1 仕様は Microsoft JDBC Driver 4.2 for SQL Server によってサポートされ、以下の API メソッドが実装されています。  
  
 **SQLServerConnection クラス**  
  
|新しいメソッド|[説明]|JDBC ドライバーの実装|  
|----------------|-----------------|--------------------------------|  
|void abort(Executor executor)|SQL Server への開いている接続を終了します。|java.sql.Connection インターフェイスの説明に従って実装されています。 詳細については、「[java.sql.Connection](http://docs.oracle.com/javase/7/docs/api/java/sql/Connection.html)」を参照してください。|  
|void setSchema(String schema)|現在の接続のスキーマを設定します。|SQL Server は、現在のセッションのスキーマの設定をサポートしていません。 このメソッドが呼び出された場合、ドライバーは警告を表示せずに、警告メッセージをログに記録します。 詳細については、「[java.sql.Connection](http://docs.oracle.com/javase/7/docs/api/java/sql/Connection.html)」を参照してください。|  
|String getSchema()|現在の接続のスキーマ名を返します。|SQL Server は、現在の接続のスキーマの設定をサポートしていないので、ドライバーは代わりにユーザーの既定のスキーマを返します。 詳細については、「[java.sql.Connection](http://docs.oracle.com/javase/7/docs/api/java/sql/Connection.html)」を参照してください。|  
  
 **SQLServerDatabaseMetaData クラス**  
  
|新しいメソッド|[説明]|JDBC ドライバーの実装|  
|----------------|-----------------|--------------------------------|  
|boolean generatedKeyAlwaysReturned()|生成されたキーの取得をドライバーがサポートしているので true を返します|Java. sql の説明に従って実装されています。 DatabaseMetaData インターフェイスです。 詳細については、「[java.sql.DatabaseMetaData](http://docs.oracle.com/javase/7/docs/api/java/sql/DatabaseMetaData.html)」をご覧ください。|  
|ResultSet getPseudoColumns(String catalog, String schemaPattern,String tableNamePattern,String columnNamePattern)|擬似/非表示の列の説明を取得します。|SQL Server には擬似列の正式な概念がないので、空の結果セットを返します。 詳細については、「[java.sql.DatabaseMetaData](http://docs.oracle.com/javase/7/docs/api/java/sql/DatabaseMetaData.html)」をご覧ください。|  
  
 **SQLServerStatement クラス**  
  
|新しいメソッド|[説明]|JDBC ドライバーの実装|  
|----------------|-----------------|--------------------------------|  
|void closeOnCompletion()|すべての依存結果セットが閉じられたときに、このステートメントが閉じられることを指定します。|Java.sql.Statement インターフェイスの説明に従って実装されています。 詳細については、「[java.sql.Statement](http://docs.oracle.com/javase/7/docs/api/java/sql/Statement.html)」をご覧ください。|  
|boolean isCloseOnCompletion()|すべての依存結果セットが閉じられたときに、このステートメントが閉じられるかどうかを示す値を返します。|Java.sql.Statement インターフェイスの説明に従って実装されています。 詳細については、「[java.sql.Statement](http://docs.oracle.com/javase/7/docs/api/java/sql/Statement.html)」をご覧ください。|  
  
 Java Database Connectivity API 4.1 仕様は Microsoft JDBC Driver 4.2 for SQL Server によってサポートされ、以下の機能が実装されています。  
  
|新機能|[説明]|  
|-----------------|-----------------|  
|新しいエスケープ関数<br /><br /> 制限された戻り行エスケープ|部分的にサポートされています。<br /><br /> エスケープ構文: 制限\<行 >[オフセット < row_offset >](using-sql-escape-sequences.md)します。|  
  
 Java Database Connectivity API 4.1 仕様は Microsoft JDBC Driver 4.2 for SQL Server によってサポートされ、以下のようにデータ型がマッピングされています。  
  
|データ型マッピング|[説明]|  
|------------------------|-----------------|  
|PreparedStatement.setObject() と PreparedStatement.setNull() メソッドで、新しいデータ型マッピングがサポートされるようになりました。|1.Java から JDBC 型への新しいマッピング<br /><br /> (a) java.math.BigInteger から JDBC BIGINT へ<br /><br /> (b) java.util.Date および java.util.Calendar から JDBC TIMESTAMP へ<br /><br /> 2.新しいデータ型変換:<br /><br /> (a) java.math.BigInteger から CHAR、VARCHAR、LONGVARCHAR、BIGINT へ<br /><br /> (b) java.util.Date および java.util.Calendar から CHAR、VARCHAR、LONGVARCHAR、DATE, TIME、TIMESTAMP へ<br /><br /> 詳細については、JDBC 4.1 の仕様を参照してください。|  
  
  
