---
title: パラメーターのないストアド プロシージャの使用 | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e9470a6d-a758-4c56-96ec-7b37139e36a7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5430d5bc97c91357dd0e3d756e8f28f7a813467b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47820590"
---
# <a name="using-a-stored-procedure-with-no-parameters"></a>パラメーターのないストアド プロシージャの使用

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

呼び出すことができる最も簡単な種類の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ストアド プロシージャは、パラメーターを含まず、1 つの結果セットを返すプロシージャです。 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] が提供する [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) クラスを使用することで、この種類のストアド プロシージャを呼び出し、返されるデータを処理することができます。

JDBC ドライバーを使用してパラメーターのないストアド プロシージャを呼び出すときは、`call` SQL エスケープ シーケンスを使用する必要があります。 パラメーターを持たない `call` エスケープ シーケンスの構文は次のとおりです。

`{call procedure-name}`

> [!NOTE]  
> SQL エスケープ シーケンスの詳細については、次を参照してください。 [SQL エスケープ シーケンスを使用して](../../connect/jdbc/using-sql-escape-sequences.md)します。

たとえば、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] サンプル データベースで次のストアド プロシージャを作成します。

```sql
CREATE PROCEDURE GetContactFormalNames
AS  
BEGIN  
   SELECT TOP 10 Title + ' ' + FirstName + ' ' + LastName AS FormalName
   FROM Person.Contact  
END  
```

このストアド プロシージャは、1 つのデータ列を含む 1 つの結果セットを返します。このデータは、Person.Contact テーブル内の先頭から 10 件の連絡先の役職、名、および姓の組み合わせです。

次の例は、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] サンプル データベースに対して開いている接続を関数に渡し、[executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) メソッドを使用して GetContactFormalNames ストアド プロシージャを呼び出しています。

```java
public static void executeSprocNoParams(Connection con) throws SQLException {  
    try(Statement stmt = con.createStatement();) {  

        ResultSet rs = stmt.executeQuery("{call dbo.GetContactFormalNames}");  
        while (rs.next()) {  
            System.out.println(rs.getString("FormalName"));  
        }  
    }  
}
```

## <a name="see-also"></a>参照

[ストアド プロシージャでのステートメントの使用](../../connect/jdbc/using-statements-with-stored-procedures.md)
