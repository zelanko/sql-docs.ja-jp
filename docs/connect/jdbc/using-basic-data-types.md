---
title: "基本データ型の使用 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7044936-5b8c-4def-858c-28a11ef70a97
caps.latest.revision: 73
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e7333b711d828981a93c51b98b7e84fb62a7749b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="using-basic-data-types"></a>基本データ型の使用
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]を使用して、JDBC の基本データ型変換、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データ型を Java プログラミング言語によって、その逆に認識できる形式にします。 JDBC ドライバーが含まれています、JDBC 4.0 API のサポートを提供する、 **SQLXML**データ型、および、National (Unicode) データ型など**NCHAR**、 **NVARCHAR**、 **LONGNVARCHAR**、および**NCLOB**です。  
  
## <a name="data-type-mappings"></a>データ型マッピング  
 次の表に、基本的な既定のマッピング[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]JDBC、および Java プログラミング言語のデータ型。  
  
|SQL Server 型|JDBC 型 (java.sql.Types)|Java 言語型|  
|----------------------|-----------------------------------|-------------------------|  
|bigint|bigint|long|  
|binary|BINARY|byte[]|  
|bit|BIT|boolean|  
|char|CHAR|文字列|  
|date|[DATE]|java.sql.Date|  
|datetime|timestamp|java.sql.Timestamp|  
|datetime2|timestamp|java.sql.Timestamp|  
|datetimeoffset (2)|microsoft.sql.Types.DATETIMEOFFSET|microsoft.sql.DateTimeOffset|  
|decimal|[DECIMAL]|java.math.BigDecimal|  
|float|DOUBLE|倍精度浮動小数点|  
|image|LONGVARBINARY|byte[]|  
|int|INTEGER|int|  
|money|[DECIMAL]|java.math.BigDecimal|  
|nchar|CHAR<br /><br /> NCHAR (Java SE 6.0)|文字列|  
|ntext|LONGVARCHAR<br /><br /> LONGNVARCHAR (Java SE 6.0)|文字列|  
|numeric|NUMERIC|java.math.BigDecimal|  
|nvarchar|VARCHAR<br /><br /> NVARCHAR (Java SE 6.0)|文字列|  
|nvarchar(max)|VARCHAR<br /><br /> NVARCHAR (Java SE 6.0)|文字列|  
|real|REAL|float|  
|smalldatetime|timestamp|java.sql.Timestamp|  
|smallint|SMALLINT|short|  
|smallmoney|[DECIMAL]|java.math.BigDecimal|  
|text|LONGVARCHAR|文字列|  
|time|TIME (1)|java.sql.Time (1)|  
|timestamp|BINARY|byte[]|  
|tinyint|TINYINT|short|  
|udt|VARBINARY|byte[]|  
|uniqueidentifier|CHAR|文字列|  
|varbinary|VARBINARY|byte[]|  
|varbinary(max)|VARBINARY|byte[]|  
|varchar|VARCHAR|文字列|  
|varchar(max)|VARCHAR|文字列|  
|xml|LONGVARCHAR<br /><br /> LONGNVARCHAR (Java SE 6.0)|文字列<br /><br /> SQLXML|  
  
 (時間と共に java.sql.Time を使用するには 1)[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]型を設定する必要あります、 **sendTimeAsDatetime**接続プロパティを false にします。  
  
 (値をプログラムでアクセスできます 2) **datetimeoffset**で[DateTimeOffset クラス](../../connect/jdbc/reference/datetimeoffset-class.md)です。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Sqlvariant データ型は、JDBC ドライバーで現在サポートされていません。 sqlvariant データ型の列を含むテーブルからデータを取得するクエリを使用すると、例外が発生します。  
  
 以下のセクションでは、JDBC ドライバーと基本データ型の使用方法の例を示します。 Java アプリケーションで、基本データ型を使用する方法の詳細な例を参照してください。[基本データ型のサンプル](../../connect/jdbc/basic-data-types-sample.md)です。  
  
## <a name="retrieving-data-as-a-string"></a>文字列としてのデータの取得  
 文字列として表示するため、JDBC の基本データ型のいずれかにマップされるデータ ソースからデータを取得する必要があるまたは厳密に型指定されたデータが必要でない場合は、使用する場合、 [getString](../../connect/jdbc/reference/getstring-method-sqlserverresultset.md)のメソッド、 [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)クラスは、次のようにします。  
  
 [!code[JDBC#UsingBasicDataTypes1](../../connect/jdbc/codesnippet/Java/using-basic-data-types_1.java)]  
  
## <a name="retrieving-data-by-data-type"></a>データ型によるデータの取得  
 データ ソースからデータを取得する必要があるが取得されているデータの種類がわかっている場合は、get のいずれかを使用\<型 >、SQLServerResultSet のメソッド クラスとも呼ばれる、 *getter メソッド*です。 列名または列インデックスを使用するには、get\<型 > メソッドは、次のようにします。  
  
 [!code[JDBC#UsingBasicDataTypes2](../../connect/jdbc/codesnippet/Java/using-basic-data-types_2.java)]  
  
> [!NOTE]  
>  GetUnicodeStream と getBigDecimal スケール メソッドでは非推奨し、は、JDBC ドライバーではサポートされていません。  
  
## <a name="updating-data-by-data-type"></a>データ型によるデータの更新  
 データ ソースのフィールドの値を更新した場合は、更新プログラムのいずれかを使用\<型 >、SQLServerResultSet クラスのメソッドです。 次の例で、 [updateInt](../../connect/jdbc/reference/updateint-method-sqlserverresultset.md)と共にメソッドが使用される、 [updateRow](../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md)データ ソース内のデータを更新する方法。  
  
 [!code[JDBC#UsingBasicDataTypes3](../../connect/jdbc/codesnippet/Java/using-basic-data-types_3.java)]  
  
> [!NOTE]  
>  JDBC ドライバーは、127 文字を超える列名の SQL Server の列を更新できません。 列名が 127 文字を超える列を更新しようとすると、例外がスローされます。  
  
## <a name="updating-data-by-parameterized-query"></a>パラメーター化クエリによるデータの更新  
 セットのいずれかを使用して、パラメーターのデータ型を設定するには、パラメーター化クエリを使用してデータ ソース内のデータを更新する必要\<型 > のメソッド、 [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)クラスとも呼ばれる、*setter メソッド*です。 次の例で、 [prepareStatement](../../connect/jdbc/reference/preparestatement-method-sqlserverconnection.md)パラメーター化されたクエリをプリコンパイルするメソッドを使用し、 [setString](../../connect/jdbc/reference/setstring-method-sqlserverpreparedstatement.md)メソッドを使用して、する前に、パラメーターの文字列値を設定[executeUpdate](../../connect/jdbc/reference/executeupdate-method.md)メソッドが呼び出されます。  
  
 [!code[JDBC#UsingBasicDataTypes4](../../connect/jdbc/codesnippet/Java/using-basic-data-types_4.java)]  
  
 パラメーター化クエリの詳細については、次を参照してください。[パラメーターを使用して SQL ステートメントを使用して](../../connect/jdbc/using-an-sql-statement-with-parameters.md)です。  
  
## <a name="passing-parameters-to-a-stored-procedure"></a>ストアド プロシージャにパラメーターを渡す  
 名前またはインデックスでパラメーターを設定、セットのいずれかを使用した場合、ストアド プロシージャに型指定されたパラメーターを渡す、\<型 > のメソッド、 [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)クラスです。 次の例で、 [prepareCall](../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md)メソッドを使用して、ストアド プロシージャへの呼び出しを設定し、 [setString](../../connect/jdbc/reference/setstring-method-sqlservercallablestatement.md)メソッドを使用して前に、の呼び出しのパラメーターを設定、 [さらに executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md)メソッドが呼び出されます。  
  
 [!code[JDBC#UsingBasicDataTypes5](../../connect/jdbc/codesnippet/Java/using-basic-data-types_5.java)]  
  
> [!NOTE]  
>  この例では、結果セットはストアド プロシージャの実行結果で返されます。  
  
 JDBC ドライバーでストアド プロシージャと入力パラメーターの使用の詳細については、次を参照してください。[入力パラメーターを使用してストアド プロシージャを使用して](../../connect/jdbc/using-a-stored-procedure-with-input-parameters.md)です。  
  
## <a name="retrieving-parameters-from-a-stored-procedure"></a>ストアド プロシージャからのパラメーターの取得  
 ストアド プロシージャからパラメーターを取得した場合必要があります最初に登録する名前で out パラメーターまたはインデックスを使用して、 [registerOutParameter](../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md)を SQLServerCallableStatement クラスのメソッド、ストアド プロシージャへの呼び出しを実行した後、適切な変数に out パラメーター戻ります。 次の例では、prepareCall メソッドは、ストアド プロシージャへの呼び出しを設定に使用される、registerOutParameter メソッドを使用して、out パラメーターを設定し、 [setString](../../connect/jdbc/reference/setstring-method-sqlservercallablestatement.md)メソッドのパラメーター設定を使用しますexecuteQuery メソッドが呼び出される前に呼び出します。 使用して、ストアド プロシージャの out パラメーターによって返される値を取得、 [getShort](../../connect/jdbc/reference/getshort-method-sqlservercallablestatement.md)メソッドです。  
  
 [!code[JDBC#UsingBasicDataTypes6](../../connect/jdbc/codesnippet/Java/using-basic-data-types_6.java)]  
  
> [!NOTE]  
>  out パラメーターが返されるだけでなく、ストアド プロシージャの実行結果により作成された結果セットが返されることもあります。  
  
 ストアド プロシージャと出力パラメーターで JDBC ドライバーを使用する方法の詳細については、次を参照してください。[出力パラメーターを持つストアド プロシージャを使用して](../../connect/jdbc/using-a-stored-procedure-with-output-parameters.md)です。  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーのデータ型をについてください。](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  

