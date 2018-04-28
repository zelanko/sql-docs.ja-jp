---
title: 出力パラメーターを使用してストアド プロシージャを使用して |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1c006f27-7e99-43d5-974c-7b782659290c
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Active
ms.openlocfilehash: adc77f65d20f409d0ad2ff115031d02888876863
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="using-a-stored-procedure-with-output-parameters"></a>出力パラメーターがあるストアド プロシージャの使用
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  A[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]呼び出すことができるストアド プロシージャは、少なくとも 1 つ返すまたは呼び出し元のアプリケーション状態に戻す複数 OUT パラメーターにデータを返すストアド プロシージャを使用するパラメーターです。 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]提供、 [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)クラスは、この種類のストアド プロシージャを呼び出すし、返されるデータの処理を行うこともできます。  
  
 JDBC ドライバーを使用してこの種類のストアド プロシージャを呼び出すときに行う必要があります、`call`と共に SQL エスケープ シーケンス、 [prepareCall](../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md)のメソッド、 [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)クラスです。 構文、 `call` OUT パラメーターを持つエスケープ シーケンスは、次。  
  
 `{call procedure-name[([parameter][,[parameter]]...)]}`  
  
> [!NOTE]  
>  SQL エスケープ シーケンスの詳細については、次を参照してください。 [SQL エスケープ シーケンスを使用して](../../connect/jdbc/using-sql-escape-sequences.md)です。  
  
 構築する場合、`call`エスケープ シーケンスを使用して、OUT パラメーターを指定しますか? (疑問符) 文字で指定します。 この文字は、ストアド プロシージャから返されるパラメーター値のプレースホルダーになります。 OUT パラメーターの値を指定するを使用して各パラメーターのデータ型を指定する必要があります、 [registerOutParameter](../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md)ストアド プロシージャを実行する前に、SQLServerCallableStatement クラスのメソッドです。  
  
 RegisterOutParameter メソッドで OUT パラメーターは、さらに、ネイティブのいずれかにマップ java.sql.Types に含まれる JDBC データ型のいずれかである必要がありますを指定した値[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データ型。 JDBC の詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データ型を参照してください[JDBC ドライバーのデータ型について](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)です。  
  
 RegisterOutParameter メソッドに OUT パラメーターの値を渡す際に、パラメーターが、パラメーターの順序も、ストアド プロシージャでパラメーターの名前に使用するデータ型だけでなくを指定する必要があります。 たとえば、ストアド プロシージャに 1 つの OUT パラメーターがある場合、その序数値は 1 です。ストアド プロシージャに 2 つのパラメーターがある場合、最初の序数値は 1 で、2 番目の序数値は 2 になります。  
  
> [!NOTE]  
>  JDBC ドライバーは CURSOR、SQLVARIANT、TABLE、およびタイムスタンプの使用をサポートしていません[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]OUT パラメーターとしてのデータ型します。  
  
 たとえばで次のストアド プロシージャを作成、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]サンプル データベース。  
  
```  
CREATE PROCEDURE GetImmediateManager  
   @employeeID INT,  
   @managerID INT OUTPUT  
AS  
BEGIN  
   SELECT @managerID = ManagerID   
   FROM HumanResources.Employee   
   WHERE EmployeeID = @employeeID  
END  
```  
  
 このストアド プロシージャでは 1 つの整数の OUT パラメーター (managerID) が返されます。これは、同様に整数である指定した IN パラメーター (employeeID) に基づいています。 OUT パラメーターで返される値は、HumanResources.Employee テーブルに含まれる EmployeeID に基づく ManagerID です。  
  
 次の例では、開いている接続を[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]サンプル データベースが、関数に渡されたと[実行](../../connect/jdbc/reference/execute-method-sqlserverstatement.md)GetImmediateManager ストアド プロシージャを呼び出すメソッドを使用します。  
  
```  
public static void executeStoredProcedure(Connection con) {  
   try {  
      CallableStatement cstmt = con.prepareCall("{call dbo.GetImmediateManager(?, ?)}");  
      cstmt.setInt(1, 5);  
      cstmt.registerOutParameter(2, java.sql.Types.INTEGER);  
      cstmt.execute();  
      System.out.println("MANAGER ID: " + cstmt.getInt(2));  
   }  
   catch (Exception e) {  
      e.printStackTrace();  
   }  
}  
```  
  
 この例では、序数位置を使用してパラメーターを識別しています。 序数位置の代わりに名前を使用してパラメーターを識別することもできます。 次のコード例では、前の例を変更して、Java アプリケーションで名前付きパラメーターを使用する方法を示します。 パラメーター名は、ストアド プロシージャの定義内にあるパラメーター名に対応しています。  
  
```  
public static void executeStoredProcedure(Connection con) {  
   try {  
      CallableStatement cstmt = con.prepareCall("{call dbo.GetImmediateManager(?, ?)}");  
      cstmt.setInt("employeeID", 5);  
      cstmt.registerOutParameter("managerID", java.sql.Types.INTEGER);  
      cstmt.execute();  
      System.out.println("MANAGER ID: " + cstmt.getInt("managerID"));  
      cstmt.close();  
   }  
   catch (Exception e) {  
      e.printStackTrace();  
   }  
```  
  
 }  
  
> [!NOTE]  
>  これらの例では、SQLServerCallableStatement クラスの execute メソッドを使用して、ストアド プロシージャを実行します。 このメソッドを使用しているのは、ストアド プロシージャによって結果セットが返されないためです。 同じ場合、 [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md)メソッドは使用されます。  
  
 ストアド プロシージャは、更新数および複数の結果セットを返すことができます。 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]を複数の結果セットと更新数を取得する、OUT パラメーターが取得されるまで状態 JDBC 3.0 の仕様に準拠します。 アプリケーションはすべての結果セット オブジェクトを取得および更新数 CallableStatement.getter メソッドを使用して、OUT パラメーターを取得する前にします。 それ以外の場合、結果セット オブジェクトと既に取得されていない更新数は失われます、OUT パラメーターを取得するときにします。 複数の結果セットと更新数の詳細については、次を参照してください。[ストアド プロシージャを使用して、更新数を含む](../../connect/jdbc/using-a-stored-procedure-with-an-update-count.md)と[複数の結果セットを使用して](../../connect/jdbc/using-multiple-result-sets.md)です。  
  
## <a name="see-also"></a>参照  
 [ストアド プロシージャでのステートメントの使用](../../connect/jdbc/using-statements-with-stored-procedures.md)  
  
  
