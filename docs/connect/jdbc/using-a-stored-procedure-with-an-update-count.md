---
title: 更新数がストアド プロシージャの使用 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 64cf4877-5995-4bfc-8865-b7618a5c8d01
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d858b255d5bdd6ce74509d36f4d0497220350694
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="using-a-stored-procedure-with-an-update-count"></a>更新数があるストアド プロシージャの使用
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  データを変更する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ストアド プロシージャを使用して、データベース、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]提供、 [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)クラスです。 SQLServerCallableStatement クラスを使用するは、データベースに含まれているデータを変更するストアド プロシージャを呼び出すし、更新数とも呼びます、影響を受ける行の数のカウントを返します。  
  
 いずれかを使用して、ストアド プロシージャを呼び出すことができますし、SQLServerCallableStatement クラスを使用して、ストアド プロシージャへの呼び出しを設定した後、[実行](../../connect/jdbc/reference/execute-method-sqlserverstatement.md)または[executeUpdate](../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md)メソッドです。 ExecuteUpdate メソッドを返します、 **int** execute メソッドは、ストアド プロシージャでは、影響を受ける行の数を表す値は変わりません。 Execute メソッドを使用する場合に、影響を受ける行の数のカウントを取得するを呼び出すことができます、 [getUpdateCount](../../connect/jdbc/reference/getupdatecount-method-sqlserverstatement.md)ストアド プロシージャを実行した後のメソッドです。  
  
> [!NOTE]  
>  JDBC ドライバで、発生した可能性があるすべてのトリガが返した更新数を含む、すべての更新数を返す場合、lastUpdateCount 接続文字列プロパティを "false" に設定します。 LastUpdateCount プロパティの詳細については、次を参照してください。[接続プロパティの設定](../../connect/jdbc/setting-the-connection-properties.md)です。  
  
 例として、次のテーブルとストアド プロシージャを作成し、サンプル データを挿入、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]サンプル データベース。  
  
```  
CREATE TABLE TestTable   
   (Col1 int IDENTITY,   
    Col2 varchar(50),   
    Col3 int);  
  
CREATE PROCEDURE UpdateTestTable  
   @Col2 varchar(50),  
   @Col3 int  
AS  
BEGIN  
   UPDATE TestTable  
   SET Col2 = @Col2, Col3 = @Col3  
END;  
INSERT INTO dbo.TestTable (Col2, Col3) VALUES ('b', 10);  
```  
  
 次の例では、開いている接続を[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]サンプル データベースが関数に渡された、UpdateTestTable ストアド プロシージャを呼び出して、execute メソッドを使用し、getUpdateCount メソッドが使用される行の数を返すストアド プロシージャを受けます。  
  
 [!code[JDBC#UsingSprocWithUpdateCount1](../../connect/jdbc/codesnippet/Java/using-a-stored-procedure_0_1.java)]  
  
## <a name="see-also"></a>参照  
 [ストアド プロシージャでのステートメントの使用](../../connect/jdbc/using-statements-with-stored-procedures.md)  
  
  
