---
title: "SQL エスケープ シーケンスの使用 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00f9e25a-088e-4ac6-aa75-43eacace8f03
caps.latest.revision: 25
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 56610f09ea40942988e88202ac09ec6a3a5e48e0
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="using-sql-escape-sequences"></a>SQL エスケープ シーケンスの使用
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] JDBC API で定義された SQL エスケープ シーケンスの使用をサポートします。 SQL ステートメント内のエスケープ シーケンスは、SQL 文字列のエスケープ部分を異なる方法で処理することを、JDBC ドライバーに指示するために使用します。 JDBC ドライバーが SQL 文字列のエスケープ部分を処理すると、文字列の該当部分は SQL Server が理解する SQL コードに変換されます。  
  
 JDBC API で要求されるエスケープ シーケンスには 5 つの種類があり、すべて JDBC ドライバーによってサポートされています。  
  
-   LIKE ワイルドカード リテラル  
  
-   関数の処理  
  
-   日付および時刻のリテラル  
  
-   ストアド プロシージャ呼び出し  
  
-   外部結合  
  
-   LIMIT エスケープ構文  
  
 JDBC ドライバーで使用されるエスケープ シーケンスの構文は、次のとおりです。  
  
 `{keyword ...parameters...}`  
  
> [!NOTE]  
>  SQL のエスケープ処理は、JDBC ドライバーに対して常に有効化されています。  
  
 以下のセクションでは、5 つの種類のエスケープ シーケンスと、それらが JDBC ドライバーでどのようにサポートされているかについて説明します。  
  
## <a name="like-wildcard-literals"></a>LIKE ワイルドカード リテラル  
 JDBC ドライバーのサポート、`{escape 'escape character'}`リテラルとして LIKE 句でワイルドカードを使用するための構文。 たとえば次のコードでは、col2 の値が (ワイルドカードとしてではなく) 文字どおりアンダースコアで始まっている行の col3 の値が返されます。  
  
```  
ResultSet rst = stmt.executeQuery("SELECT col3 FROM test1 WHERE col2   
LIKE '\\_%' {escape '\\'}");  
```  
  
> [!NOTE]  
>  エスケープ シーケンスは、SQL ステートメントの末尾に置く必要があります。 コマンド文字列内に複数の SQL ステートメントがある場合、エスケープ シーケンスは該当する各 SQL ステートメントの末尾に置く必要があります。  
  
## <a name="function-handling"></a>関数処理  
 JDBC ドライバーは、次の構文で SQL ステートメント内の関数エスケープ シーケンスをサポートしています。  
  
```  
{fn functionName}  
```  
  
 ここで`functionName`JDBC ドライバーでサポートされる関数。 例:  
  
```  
SELECT {fn UCASE(Name)} FROM Employee  
```  
  
 次の表は、JDBC ドライバーで関数エスケープ シーケンスを使用する場合にサポートされている、さまざまな関数を示します。  
  
|文字列関数|数値関数|日付時刻関数|システム関数|  
|----------------------|-----------------------|------------------------|----------------------|  
|ASCII<br /><br /> CHAR<br /><br /> CONCAT<br /><br /> DIFFERENCE<br /><br /> INSERT<br /><br /> LCASE<br /><br /> [LEFT]<br /><br /> LENGTH<br /><br /> LOCATE<br /><br /> [LTRIM]<br /><br /> REPEAT<br /><br /> [REPLACE]<br /><br /> [RIGHT]<br /><br /> [RTRIM]<br /><br /> SOUNDEX<br /><br /> Space<br /><br /> [SUBSTRING]<br /><br /> UCASE|ABS<br /><br /> ACOS<br /><br /> ASIN<br /><br /> ATAN<br /><br /> ATAN2<br /><br /> CEILING<br /><br /> COS<br /><br /> COT<br /><br /> DEGREES<br /><br /> EXP<br /><br /> FLOOR<br /><br /> LOG<br /><br /> LOG10<br /><br /> [MOD]<br /><br /> PI<br /><br /> POWER<br /><br /> RADIANS<br /><br /> RAND<br /><br /> [ROUND]<br /><br /> SIGN<br /><br /> SIN<br /><br /> SQRT<br /><br /> TAN<br /><br /> TRUNCATE|CURDATE<br /><br /> CURTIME<br /><br /> DAYNAME<br /><br /> DAYOFMONTH<br /><br /> [DAYOFWEEK]<br /><br /> DAYOFYEAR<br /><br /> EXTRACT<br /><br /> [HOUR]<br /><br /> [MINUTE]<br /><br /> [MONTH]<br /><br /> MONTHNAME<br /><br /> [NOW]<br /><br /> [QUARTER]<br /><br /> [SECOND]<br /><br /> TIMESTAMPADD<br /><br /> TIMESTAMPDIFF<br /><br /> [WEEK]<br /><br /> [YEAR]|DATABASE<br /><br /> IFNULL<br /><br /> User|  
  
> [!NOTE]  
>  データベースでサポートされていない関数を使用すると、エラーが発生します。  
  
## <a name="date-and-time-literals"></a>日付と時刻リテラル  
 日付、時刻、およびタイムスタンプのリテラルに使用するエスケープ構文は、次のとおりです。  
  
```  
{literal-type 'value'}  
```  
  
 ここで`literal-type`は、次のいずれか。  
  
|リテラルの種類|Description|値の形式|  
|------------------|-----------------|------------------|  
|d|日付|yyyy-mm-dd|  
|t|[時刻]|hh:mm:ss [1]|  
|ts|TimeStamp|yyyy-mm-dd hh:mm:ss[.f...]|  
  
 例:  
  
```  
UPDATE Orders SET OpenDate={d '2005-01-31'}   
WHERE OrderID=1025  
```  
  
## <a name="stored-procedure-calls"></a>ストアド プロシージャ呼び出し  
 JDBC ドライバーのサポート、`{? = call proc_name(?,...)}`と`{call proc_name(?,...)}`戻り値パラメーターを処理する必要があるかどうかによって、ストアド プロシージャを呼び出すのための構文をエスケープします。  
  
 プロシージャは、データベースに格納されている実行可能なオブジェクトです。 これは通常、プリコンパイルされた 1 つ以上の SQL ステートメントです。 ストアド プロシージャを呼び出すためのエスケープ シーケンス構文は、次のとおりです。  
  
```  
{[?=]call procedure-name[([parameter][,[parameter]]...)]}  
```  
  
 ここで`procedure-name`ストアド プロシージャの名前を指定し、`parameter`ストアド プロシージャのパラメーターを指定します。  
  
 使用しての詳細については、`call`エスケープ シーケンス ストアド プロシージャでは、「[ストアド プロシージャを使用してステートメント](../../connect/jdbc/using-statements-with-stored-procedures.md)です。  
  
## <a name="outer-joins"></a>外部結合  
 JDBC ドライバーでは、SQL92 の左外部結合、右外部結合、および完全外部結合で使用する構文がサポートされています。 外部結合用のエスケープ シーケンスは、次のとおりです。  
  
```  
{oj outer-join}  
```  
  
 outer-join の内容は次のとおりです。  
  
```  
table-reference {LEFT | RIGHT | FULL} OUTER JOIN    
{table-reference | outer-join} ON search-condition  
```  
  
 ここで`table-reference`テーブル名と`search-condition`テーブルで使用する結合条件です。  
  
 例:  
  
```  
SELECT Customers.CustID, Customers.Name, Orders.OrderID, Orders.Status   
   FROM {oj Customers LEFT OUTER JOIN   
      Orders ON Customers.CustID=Orders.CustID}   
   WHERE Orders.Status='OPEN'  
```  
  
 JDBC ドライバーでは、次の外部結合エスケープ シーケンスがサポートされています。  
  
-   左外部結合  
  
-   右外部結合  
  
-   完全外部結合  
  
-   入れ子になった外部結合  
  
## <a name="limit-escape-syntax"></a>Limit エスケープ構文  
  
> [!NOTE]  
>  LIMIT エスケープ構文のみサポートされます Microsoft JDBC Driver 4.2 で (またはそれ以上) for SQL Server JDBC 4.1 以降を使用する場合。  
  
 LIMIT のエスケープ構文は次のとおりです。  
  
```  
LIMIT <rows> [OFFSET <row offset>]  
```  
  
 エスケープ構文は、2 つの部分を持つ: \<*行*> は必須で、返す行の数を指定します。 オフセットおよび\<*行オフセット*> オプションで、行を返すを開始する前にスキップする行の数を指定します。 JDBC ドライバーでは、このうち必須の部分のみがサポートされ、LIMIT の代わりに TOP を使用するようにクエリを変換して処理されます。 SQL Server は、LIMIT 句をサポートしていません。 **JDBC ドライバーは、省略可能なできません\<行オフセット > を使用する場合に、ドライバーが例外をスローおよび**です。  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーでステートメントを使用します。](../../connect/jdbc/using-statements-with-the-jdbc-driver.md)  
  
  

