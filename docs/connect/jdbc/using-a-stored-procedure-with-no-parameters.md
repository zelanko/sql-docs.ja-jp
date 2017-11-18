---
title: "パラメーターなしのストアド プロシージャを使って |Microsoft ドキュメント"
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
ms.assetid: e9470a6d-a758-4c56-96ec-7b37139e36a7
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 4600b2cd527fdb6261ca700a19bf2e5c004bc31c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="using-a-stored-procedure-with-no-parameters"></a>パラメーターのないストアド プロシージャの使用
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  最も単純な種類の[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]呼び出すことができるストアド プロシージャであるパラメーターが含まれていないと、1 つの結果セットを返します。 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]提供、 [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)クラスは、この種類のストアド プロシージャを呼び出すし、返されるデータの処理を行うこともできます。  
  
 JDBC ドライバーを使用してパラメーターなしのストアド プロシージャを呼び出すときに行う必要があります、 `call` SQL エスケープ シーケンスです。 構文、`call`パラメーターなしのエスケープ シーケンスのとおりです。  
  
 `{call procedure-name}`  
  
> [!NOTE]  
>  SQL エスケープ シーケンスの詳細については、次を参照してください。 [SQL エスケープ シーケンスを使用して](../../connect/jdbc/using-sql-escape-sequences.md)です。  
  
 たとえばで次のストアド プロシージャを作成、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]サンプル データベース。  
  
```  
CREATE PROCEDURE GetContactFormalNames   
AS  
BEGIN  
   SELECT TOP 10 Title + ' ' + FirstName + ' ' + LastName AS FormalName   
   FROM Person.Contact  
END  
```  
  
 このストアド プロシージャは、1 つのデータ列を含む 1 つの結果セットを返します。このデータは、Person.Contact テーブル内の先頭から 10 件の連絡先の役職、名、および姓の組み合わせです。  
  
 次の例では、開いている接続を[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]サンプル データベースが、関数に渡されたと[executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) GetContactFormalNames ストアド プロシージャを呼び出すメソッドを使用します。  
  
```  
public static void executeSprocNoParams(Connection con) {  
   try {  
      Statement stmt = con.createStatement();  
      ResultSet rs = stmt.executeQuery("{call dbo.GetContactFormalNames}");  
  
      while (rs.next()) {  
         System.out.println(rs.getString("FormalName"));  
      }  
      rs.close();  
      stmt.close();  
   }  
   catch (Exception e) {  
      e.printStackTrace();  
   }  
}  
```  
  
## <a name="see-also"></a>参照  
 [ストアド プロシージャでステートメントを使用](../../connect/jdbc/using-statements-with-stored-procedures.md)  
  
  

