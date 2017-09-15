---
title: "についてのデータ型の変換 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98fa7488-aac3-45b4-8aa4-83ed6ab638b4
caps.latest.revision: 34
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b8a4439d9682435baca0867dfc9d8bd96d0fcd7c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="understanding-data-type-conversions"></a>データ型変換について
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Java プログラミング言語のデータ型への変換を容易にする[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データ型、 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] JDBC の仕様で必要なデータ型変換を提供します。 柔軟性を高め、すべての型を変換できるとの間**オブジェクト**、**文字列**、および**byte[]**データ型。  
  
## <a name="getter-method-conversions"></a>getter メソッドの変換  
 に基づいて、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データ型場合、次の図にはには、get、JDBC ドライバーの変換マップが含まれています\<型 > () メソッドの、 [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)クラス、および getのサポートされている変換。\<型 > のメソッド、 [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)クラスです。  
  
 ![JDBCGetterConversions](../../connect/jdbc/media/jdbcgetterconversions.gif "JDBCGetterConversions")  
  
 JDBC ドライバーの getter メソッドでサポートされている変換には、次の 3 つのカテゴリがあります。  
  
-   **非データ損失 (x)**: getter 型が同じ場合の変換または基になるサーバーの種類より小さくします。 たとえばを呼び出すとき getBigDecimal 基になるサーバーの decimal 列で、変換は必要ありません。  
  
-   **変換 (y)**: サーバーの数値型から Java 言語型と、変換が通常は、Java 言語変換規則に従ってへの変換。 有効桁数が常に切り捨てられ、これらの変換を — 丸められることはありません — オーバーフローを処理し、変換先の型、サイズが小さいの剰余として。 たとえば、getInt を呼び出すことで、基になる**10 進数**「1.9999」を含む列は「1」を返しますまたは、基になる**10 進**値が「3000000000」、 **int**値をオーバーフローして"-1294967296"となります。  
  
-   **データに依存 (z)**: 基になる文字型から数値型への変換では、文字型がその型に変換できる値を含んでいる必要があります。 これ以外の変換は行われません。 値が getter 型には大きすぎる場合、その値は有効ではありません。 たとえば、「53」を含む varchar (50) 列で getInt を呼び出した場合、値が返されますとして、 **int**; 基になる値が"xyz"または「3000000000」でエラーがスローされます。  
  
 GetString に対してを呼び出した場合、**バイナリ**、 **varbinary**、 **varbinary (max)**、または**イメージ**列データ型が返される値として、16 進数の文字列値です。  
  
## <a name="updater-method-conversions"></a>updater メソッドの変換  
 型指定された更新プログラムに渡されるデータを Java\<型 > () メソッドの[SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)クラスでは、次のような変換を適用します。  
  
 ![JDBCUpdaterConversions](../../connect/jdbc/media/jdbc_jdbcupdatterconversions.gif "JDBCUpdaterConversions")  
  
 JDBC ドライバーの updater メソッドでサポートされている変換には、次の 3 つのカテゴリがあります。  
  
-   **非データ損失 (x)**: updater 型が同じ場合の変換または基になるサーバーの種類より小さくします。 たとえば、基になるサーバーの decimal 列で updateBigDecimal を呼び出すとき、変換は必要ありません。  
  
-   **変換 (y)**: サーバーの数値型から Java 言語型と、変換が通常は、Java 言語変換規則に従ってへの変換。 これらの変換では、有効桁数は四捨五入されることはなく常に切り捨てられます。オーバーフローは変換後の型の剰余として処理され、変換前より小さくなります。 たとえば、updateDecimal を呼び出すことで、基になる**int** 「1.9999」を含む列は「1」を返しますまたは、基になる**10 進**値が「3000000000」、 **int**値をオーバーフローして"-1294967296"となります。  
  
-   **データに依存 (z)**: 基になるソースのデータ型から別のデータ型への変換が含まれている値を変換先の型に変換できることを必要とします。 これ以外の変換は行われません。 値が getter 型には大きすぎる場合、その値は有効ではありません。 たとえば、"53" が格納された int 列に対して updateString を呼び出した場合、更新は成功しますが、基になる文字列値が "foo" や "3000000000" であった場合は、エラーがスローされます。  
  
 に対して updateString を呼び出したときに、**バイナリ**、 **varbinary**、 **varbinary (max)**、または**イメージ**文字列値を処理する列のデータ型、16 進数文字列値です。  
  
 ときに、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]列データ型が**XML**、データ値を有効にする必要があります**XML**です。 UpdateBytes、updateBinaryStream、updateBlob メソッドを呼び出すときにデータ値は XML 文字の 16 進数文字列形式にする必要があります。 例:  
  
```  
<hello>world</hello> = 0x3C68656C6C6F3E776F726C643C2F68656C6C6F3E   
```  
  
 XML 文字に特定の文字エンコードが使用されている場合は、バイト順マーク (BOM) が必要です。  
  
## <a name="setter-method-conversions"></a>setter メソッドの変換  
 Java で型指定されたセットに渡されるデータ\<型 > () メソッドの[SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)クラスおよび[SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)クラスでは、次のような変換を適用します。  
  
 ![JDBCSetterConversions](../../connect/jdbc/media/jdbc_jdbcsetterconversions_v2.gif "JDBCSetterConversions")  
  
 サーバーはすべての変換を試みて、変換に失敗した場合はエラーを返します。  
  
 場合、**文字列**データ型、値の長さを超えた場合**VARCHAR**、マップ先**LONGVARCHAR**です。 同様に、 **NVARCHAR**にマップ**LONGNVARCHAR**値のサポートされている長さを超えた場合**NVARCHAR**です。 場合も同様です**byte[]**です。 も長い値**VARBINARY**になる**LONGVARBINARY**です。  
  
 JDBC ドライバーの setter メソッドでサポートされている変換には、次の 2 つのカテゴリがあります。  
  
-   **非データ損失 (x)**: setter 型が同じ数値の場合の変換または基になるサーバーの種類より小さくします。 たとえば、基になるサーバー setBigDecimal を呼び出すときに**decimal**列で、変換は必要ありません。 数値を文字の場合、Java**数値**データ型を変換、**文字列**です。 たとえば、varchar (50) 列で「53」の値を持つ setDouble を呼び出すには、その変換先列に文字列値「53」が生成されます。  
  
-   **変換 (y)**: Java から変換**数値**の種類を基になるサーバー**数値**型より小さいです。 この変換は通常と依存[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]変換規則です。 有効桁数は常に切り捨てられます (決して丸みのある) と、オーバーフローがサポートされない変換エラーをスローします。 たとえば、updateDecimal を使用して、変換先の列に「1」の基になる整数列の結果では、「1.9999」の値を持つ「3000000000」が渡される場合、ドライバーはエラーをスローします。  
  
-   **データに依存 (z)**: Java から変換**文字列**基になる型[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データ型は、次の条件によって異なります: ドライバーの送信、**文字列**値です。[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]と[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]必要な場合、変換を実行します。 SendStringParametersAsUnicode が true に設定され、基になる場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データ型は**イメージ**、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]変換が許可されず**nvarchar**に**イメージ**と、SQLServerException がスローされます。 SendStringParametersAsUnicode が false と、基になるに設定されている場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データ型は**イメージ**、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]の変換が許可**varchar**に**イメージ**され、例外はスローされません。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]変換を行い、問題がある場合、JDBC ドライバーにエラーを渡します。  
  
 ときに、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]列データ型が**XML**、データ値を有効にする必要があります**XML**です。 UpdateBytes、updateBinaryStream、updateBlob メソッドを呼び出すときにデータ値は XML 文字の 16 進数文字列形式にする必要があります。 例:  
  
```  
<hello>world</hello> = 0x3C68656C6C6F3E776F726C643C2F68656C6C6F3E   
```  
  
 XML 文字に特定の文字エンコードが使用されている場合は、バイト順マーク (BOM) が必要です。  
  
## <a name="conversions-on-setobject"></a>setObject での変換  
  
> [!NOTE]  
>  Microsoft JDBC Drivers 4.2 (以降) SQL Server は、JDBC 4.1 と 4.2 をサポートしています。 4.1 および 4.2 のデータ型マッピングと変換の詳細については、次を参照してください。 [JDBC Driver の JDBC 4.1 準拠](../../connect/jdbc/jdbc-4-1-compliance-for-the-jdbc-driver.md)と[JDBC Driver の JDBC 4.2 準拠](../../connect/jdbc/jdbc-4-2-compliance-for-the-jdbc-driver.md)、以下の情報だけでなくです。  
  
 Java で型指定された、setObject に渡されるデータ (\<型 >) のメソッド、 [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)クラスでは、次のような変換を適用します。  
  
 ![JDBCSetObjectConversions](../../connect/jdbc/media/jdbc_jdbcsetobjectconversions.gif "JDBCSetObjectConversions")  
  
 指定されたターゲットの型がないと setObject メソッドでは、既定のマッピングを使用します。 場合、**文字列**データ型、値の長さを超えた場合**VARCHAR**、マップ先**LONGVARCHAR**です。 同様に、 **NVARCHAR**にマップ**LONGNVARCHAR**値のサポートされている長さを超えた場合**NVARCHAR**です。 場合も同様です**byte[]**です。 も長い値**VARBINARY**になる**LONGVARBINARY**です。  
  
 JDBC ドライバーの setObject メソッドでサポートされている変換には、次の 3 つのカテゴリがあります。  
  
-   **非データ損失 (x)**: setter 型が同じ数値の場合の変換または基になるサーバーの種類より小さくします。 たとえば、基になるサーバー setBigDecimal を呼び出すときに**decimal**列で、変換は必要ありません。 数値を文字の場合、Java**数値**データ型を変換、**文字列**です。 たとえば、varchar (50) 列で「53」の値を持つ setDouble を呼び出すと、その変換先列に文字列値「53」が生成されます。  
  
-   **変換 (y)**: Java から変換**数値**の種類を基になるサーバー**数値**型より小さいです。 この変換は通常と依存[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]変換規則です。 有効桁数は常に切り捨てられ、四捨五入されることはありません。オーバーフローするとサポートされていない変換のエラーがスローされます。 たとえば、updateDecimal を使用して、変換先の列に「1」の基になる整数列の結果では、「1.9999」の値を持つ「3000000000」が渡される場合、ドライバーはエラーをスローします。  
  
-   **データに依存 (z)**: Java から変換**文字列**基になる型[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データ型は、次の条件によって異なります: ドライバーの送信、**文字列**値です。[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]と[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]必要な場合、変換を実行します。 SendStringParametersAsUnicode 接続プロパティが true に設定され、基になる場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データ型は**イメージ**、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]変換が許可されず**nvarchar** に**イメージ**と、SQLServerException がスローされます。 SendStringParametersAsUnicode が false と、基になるに設定されている場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データ型は**イメージ**、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]の変換が許可**varchar**に**イメージ**され、例外はスローされません。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]一括して設定の変換を実行し、問題がある場合、JDBC ドライバーにエラーを渡します。 クライアント側変換の例外し、のみの場合に実行されます**日付**、**時間**、**タイムスタンプ**、**ブール**、および**文字列**値。  
  
 ときに、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]列データ型が**XML**、データ値を有効にする必要があります**XML**です。 setObject(byte[], SQLXML)、setObject(inputStream, SQLXML)、setObject(Blob, SQLXML) のいずれかのメソッドを呼び出す場合、データ値は、XML 文字の 16 進形式の文字列表記である必要があります。 例:  
  
```  
<hello>world</hello> = 0x3C68656C6C6F3E776F726C643C2F68656C6C6F3E   
```  
  
 XML 文字に特定の文字エンコードが使用されている場合は、バイト順マーク (BOM) が必要です。  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーのデータ型をについてください。](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  
