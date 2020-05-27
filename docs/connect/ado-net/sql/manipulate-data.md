---
title: データの操作
description: MARS アプリケーションのコーディングの例を示します。
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 51096a2e-8b38-4c4d-a523-799bfdb7ec69
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: a3a567d86cb70c5d6d931d631a0f744ea59d359f
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "78896692"
---
# <a name="manipulating-data"></a>データの操作

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

複数のアクティブな結果セット (MARS) を導入する場合は、開発者が事前に複数の接続またはサーバー側のカーソルを使用して、特定のシナリオを解決しておく必要がありました。 さらに、トランザクションの状況で複数の接続を使用するときは、接続をバインド (**sp_getbindtoken** と **sp_bindsession**) する必要がありました。 次のシナリオは、MARS が有効になっている接続を、複数の接続の代わりに使用する方法を示しています。  
  
## <a name="using-multiple-commands-with-mars"></a>MARS を使った複数コマンドの使用  
次のコンソール アプリケーションは、MARS を有効にして、2 つの <xref:Microsoft.Data.SqlClient.SqlCommand> オブジェクトと 1 つの <xref:Microsoft.Data.SqlClient.SqlConnection> オブジェクトを使って、2 つの <xref:Microsoft.Data.SqlClient.SqlDataReader> オブジェクトを使用する方法を示しています。  
  
### <a name="example"></a>例  
この例では、**AdventureWorks** データベースへの 1 つの接続を開きます。 <xref:Microsoft.Data.SqlClient.SqlCommand> オブジェクトを使用することで、<xref:Microsoft.Data.SqlClient.SqlDataReader> が作成されます。 そのリーダーが使用されるとき、最初の <xref:Microsoft.Data.SqlClient.SqlDataReader> のデータが 2 番目のリーダーの WHERE 句への入力として使用され、2 番目の <xref:Microsoft.Data.SqlClient.SqlDataReader> が開きます。  
  
> [!NOTE]
>  次の例では、SQL Server に含まれるサンプルの **AdventureWorks** データベースを使用します。 サンプル コードに示されている接続文字列では、データベースがローカル コンピューターにインストールされ、使用可能であることを前提としています。 実際の環境では必要に応じて接続文字列を変更してください。  
  
```csharp  
using System;  
using System.Data;  
using Microsoft.Data.SqlClient;  
  
class Class1  
{  
static void Main()  
{  
  // By default, MARS is disabled when connecting  
  // to a MARS-enabled host.  
  // It must be enabled in the connection string.  
  string connectionString = GetConnectionString();  
  
  int vendorID;  
  SqlDataReader productReader = null;  
  string vendorSQL =   
    "SELECT VendorId, Name FROM Purchasing.Vendor";  
  string productSQL =   
    "SELECT Production.Product.Name FROM Production.Product " +  
    "INNER JOIN Purchasing.ProductVendor " +  
    "ON Production.Product.ProductID = " +   
    "Purchasing.ProductVendor.ProductID " +  
    "WHERE Purchasing.ProductVendor.VendorID = @VendorId";  
  
  using (SqlConnection awConnection =   
    new SqlConnection(connectionString))  
  {  
    SqlCommand vendorCmd = new SqlCommand(vendorSQL, awConnection);  
    SqlCommand productCmd =   
      new SqlCommand(productSQL, awConnection);  
  
    productCmd.Parameters.Add("@VendorId", SqlDbType.Int);  
  
    awConnection.Open();  
    using (SqlDataReader vendorReader = vendorCmd.ExecuteReader())  
    {  
      while (vendorReader.Read())  
      {  
        Console.WriteLine(vendorReader["Name"]);  
  
        vendorID = (int)vendorReader["VendorId"];  
  
        productCmd.Parameters["@VendorId"].Value = vendorID;  
        // The following line of code requires  
        // a MARS-enabled connection.  
        productReader = productCmd.ExecuteReader();  
        using (productReader)  
        {  
          while (productReader.Read())  
          {  
            Console.WriteLine("  " +  
              productReader["Name"].ToString());  
          }  
        }  
      }  
  }  
      Console.WriteLine("Press any key to continue");  
      Console.ReadLine();  
    }  
  }  
  private static string GetConnectionString()  
  {  
    // To avoid storing the connection string in your code,  
    // you can retrieve it from a configuration file.  
    return "Data Source=(local);Integrated Security=SSPI;" +   
      "Initial Catalog=AdventureWorks;MultipleActiveResultSets=True";  
  }  
}  
```  
  
## <a name="reading-and-updating-data-with-mars"></a>MARS を使用した読み取りと更新  
MARS を使用すると、複数の保留中の操作を使用して、読み取り操作およびデータ操作言語 (DML) 操作の両方に対して接続を使用できます。 この機能により、アプリケーションが接続ビジー エラーを処理する必要がなくなります。 さらに、MARS によって、通常多くのリソースを消費するサーバー側カーソルのユーザーを置き換えることができます。 最後に、複数の操作を単一の接続で実行できるので、同じトランザクション コンテキストを共有することにより、システムのストアド プロシージャである **sp_getbindtoken** と **sp_bindsession** を使用する必要がなくなります。  
  
### <a name="example"></a>例  
次のコンソール アプリケーションは、MARS を有効にして、3 つの <xref:Microsoft.Data.SqlClient.SqlCommand> オブジェクトと 1 つの <xref:Microsoft.Data.SqlClient.SqlConnection> オブジェクトを使って、2 つの <xref:Microsoft.Data.SqlClient.SqlDataReader> オブジェクトを使用する方法を示しています。 最初のコマンド オブジェクトは、信用格付けの評価が 5 であるベンダーの一覧を取得します。 2 番目のコマンド オブジェクトは、<xref:Microsoft.Data.SqlClient.SqlDataReader> から提供されているベンダー ID を使用して、特定のベンダーの全製品を含む 2 番目の <xref:Microsoft.Data.SqlClient.SqlDataReader> を読み込みます。 各製品レコードには、2 番目の <xref:Microsoft.Data.SqlClient.SqlDataReader> によってアクセスされます。 計算が実行され、新規 **OnOrderQty** を判定します。 3 番目のコマンド オブジェクトでは、**ProductVendor** テーブルを新しい値で更新します。 このプロセスはすべて 1 つのトランザクション内で実行され、最後にロールバックされます。  
  
> [!NOTE]
>  次の例では、SQL Server に含まれるサンプルの **AdventureWorks** データベースを使用します。 サンプル コードに示されている接続文字列では、データベースがローカル コンピューターにインストールされ、使用可能であることを前提としています。 実際の環境では必要に応じて接続文字列を変更してください。  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.Data;  
using Microsoft.Data.SqlClient;  
  
class Program  
{  
static void Main()  
{  
  // By default, MARS is disabled when connecting  
  // to a MARS-enabled host.  
  // It must be enabled in the connection string.  
  string connectionString = GetConnectionString();  
  
  SqlTransaction updateTx = null;  
  SqlCommand vendorCmd = null;  
  SqlCommand prodVendCmd = null;  
  SqlCommand updateCmd = null;  
  
  SqlDataReader prodVendReader = null;  
  
  int vendorID = 0;  
  int productID = 0;  
  int minOrderQty = 0;  
  int maxOrderQty = 0;  
  int onOrderQty = 0;  
  int recordsUpdated = 0;  
  int totalRecordsUpdated = 0;  
  
  string vendorSQL =  
      "SELECT VendorID, Name FROM Purchasing.Vendor " +   
      "WHERE CreditRating = 5";  
  string prodVendSQL =  
      "SELECT ProductID, MaxOrderQty, MinOrderQty, OnOrderQty " +  
      "FROM Purchasing.ProductVendor " +   
      "WHERE VendorID = @VendorID";  
  string updateSQL =  
      "UPDATE Purchasing.ProductVendor " +   
      "SET OnOrderQty = @OrderQty " +  
      "WHERE ProductID = @ProductID AND VendorID = @VendorID";  
  
  using (SqlConnection awConnection =   
    new SqlConnection(connectionString))  
  {  
    awConnection.Open();  
    updateTx = awConnection.BeginTransaction();  
  
    vendorCmd = new SqlCommand(vendorSQL, awConnection);  
    vendorCmd.Transaction = updateTx;  
  
    prodVendCmd = new SqlCommand(prodVendSQL, awConnection);  
    prodVendCmd.Transaction = updateTx;  
    prodVendCmd.Parameters.Add("@VendorId", SqlDbType.Int);  
  
    updateCmd = new SqlCommand(updateSQL, awConnection);  
    updateCmd.Transaction = updateTx;  
    updateCmd.Parameters.Add("@OrderQty", SqlDbType.Int);  
    updateCmd.Parameters.Add("@ProductID", SqlDbType.Int);  
    updateCmd.Parameters.Add("@VendorID", SqlDbType.Int);  
  
    using (SqlDataReader vendorReader = vendorCmd.ExecuteReader())  
    {  
      while (vendorReader.Read())  
      {  
        Console.WriteLine(vendorReader["Name"]);  
  
        vendorID = (int) vendorReader["VendorID"];  
        prodVendCmd.Parameters["@VendorID"].Value = vendorID;  
        prodVendReader = prodVendCmd.ExecuteReader();  
  
        using (prodVendReader)  
        {  
          while (prodVendReader.Read())  
          {  
            productID = (int) prodVendReader["ProductID"];  
  
            if (prodVendReader["OnOrderQty"] == DBNull.Value)  
            {  
              minOrderQty = (int) prodVendReader["MinOrderQty"];  
              onOrderQty = minOrderQty;  
            }  
            else  
            {  
              maxOrderQty = (int) prodVendReader["MaxOrderQty"];  
              onOrderQty = (int)(maxOrderQty / 2);  
            }  
  
            updateCmd.Parameters["@OrderQty"].Value = onOrderQty;  
            updateCmd.Parameters["@ProductID"].Value = productID;  
            updateCmd.Parameters["@VendorID"].Value = vendorID;  
  
            recordsUpdated = updateCmd.ExecuteNonQuery();  
            totalRecordsUpdated += recordsUpdated;  
          }  
        }  
      }  
    }  
    Console.WriteLine("Total Records Updated: " +   
      totalRecordsUpdated.ToString());  
    updateTx.Rollback();  
    Console.WriteLine("Transaction Rolled Back");  
  }  
  
  Console.WriteLine("Press any key to continue");  
  Console.ReadLine();  
}  
private static string GetConnectionString()  
{  
  // To avoid storing the connection string in your code,  
  // you can retrieve it from a configuration file.  
  return "Data Source=(local);Integrated Security=SSPI;" +   
    "Initial Catalog=AdventureWorks;" +   
    "MultipleActiveResultSets=True";  
  }  
}  
```  
  
## <a name="next-steps"></a>次のステップ
- [複数のアクティブな結果セット (MARS)](multiple-active-result-sets-mars.md)
