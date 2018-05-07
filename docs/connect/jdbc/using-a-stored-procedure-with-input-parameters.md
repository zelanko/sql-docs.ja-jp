---
title: 入力パラメーターを使用してストアド プロシージャを使用して |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 8f491b70-7d1b-42bd-964f-9a8b86af5eaa
caps.latest.revision: 21
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f736e2e901d17d4a6b8d114964a315afd389ab9e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="using-a-stored-procedure-with-input-parameters"></a>入力パラメーターがあるストアド プロシージャの使用
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  A[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]呼び出すことができるストアド プロシージャは、いずれかを含む 1 つまたは複数パラメーターでは、ストアド プロシージャにデータを渡すために使用できるパラメーター。 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]提供、 [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)クラスは、この種類のストアド プロシージャを呼び出すと、返されるデータを処理を行うこともできます。  
  
 使用する必要がありますをパラメーターで使用してストアド プロシージャを呼び出して、JDBC ドライバーを使用する場合、`call`と共に SQL エスケープ シーケンス、 [prepareCall](../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md)のメソッド、 [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)クラスです。 構文、`call`パラメーターを持つエスケープ シーケンスのとおりです。  
  
 `{call procedure-name[([parameter][,[parameter]]...)]}`  
  
> [!NOTE]  
>  SQL エスケープ シーケンスの詳細については、次を参照してください。 [SQL エスケープ シーケンスを使用して](../../connect/jdbc/using-sql-escape-sequences.md)です。  
  
 構築する場合、`call`エスケープ シーケンスを使用して、IN パラメーターを指定しますか? (疑問符) 文字で指定します。 この文字は、ストアド プロシージャに渡されるパラメーター値のプレースホルダーになります。 パラメーターの値を指定するには、SQLServerPreparedStatement クラスの setter メソッドのいずれかを行うこともできます。 使用できる setter メソッドは、IN パラメーターのデータ型で決まります。  
  
 setter メソッドに値を渡す場合は、パラメーターで使用する実際の値だけでなく、ストアド プロシージャ内のパラメーターの順序も指定する必要があります。 たとえば、ストアド プロシージャに IN パラメーターが 1 つ存在する場合、その序数値は 1 になります。 ストアド プロシージャに 2 つのパラメーターが存在する場合、1 つ目の序数値は 1 に、2 つ目の序数値は 2 になります。  
  
 IN パラメーターを含むストアド プロシージャを呼び出す方法の例とで uspGetEmployeeManagers ストアド プロシージャを使用して、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]サンプル データベース。 このストアド プロシージャは EmployeeID という名前の入力パラメーターを 1 つ受け入れます。このパラメーターは整数値で、指定された EmployeeID に基づいて従業員およびそのマネージャーの再帰的にリストを返します。 このストアド プロシージャの Java コードは次のとおりです。  
  
```  
public static void executeSprocInParams(Connection con) {  
   try {  
      PreparedStatement pstmt = con.prepareStatement("{call dbo.uspGetEmployeeManagers(?)}");  
      pstmt.setInt(1, 50);  
      ResultSet rs = pstmt.executeQuery();  
  
      while (rs.next()) {  
         System.out.println("EMPLOYEE:");  
         System.out.println(rs.getString("LastName") + ", " + rs.getString("FirstName"));  
         System.out.println("MANAGER:");  
         System.out.println(rs.getString("ManagerLastName") + ", " + rs.getString("ManagerFirstName"));  
         System.out.println();  
      }  
      rs.close();  
      pstmt.close();  
   }  
  
   catch (Exception e) {  
      e.printStackTrace();  
    }  
}  
```  
  
## <a name="see-also"></a>参照  
 [ストアド プロシージャでのステートメントの使用](../../connect/jdbc/using-statements-with-stored-procedures.md)  
  
  
