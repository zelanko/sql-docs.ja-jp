---
title: コンソール アプリケーションでのポーリング
description: ポーリングを使用して、コンソール アプリケーションからの非同期コマンドの実行が完了するまで待機する例を示します。 この手法は、クラス ライブラリや、ユーザー インターフェイスのないその他のアプリケーションでも有効です。
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 4ff084d5-5956-4db1-8e18-c5a66b000882
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: 8d067dc5f72bb1534ec75e248fd9df34c2452f77
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80924275"
---
# <a name="polling-in-console-applications"></a>コンソール アプリケーションでのポーリング

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

ADO.NET の非同期操作を使用すると、あるスレッドの時間のかかるデータベース操作を、別のスレッドで他のタスクを実行している間に開始できます。 ただし、ほとんどの場合、データベース操作が完了するまでの間に、アプリケーションの処理を続行してはいけないポイントに最終的に到達します。 このような場合は、非同期操作をポーリングして操作が完了したかどうかを判断すると便利です。  
  
<xref:System.IAsyncResult.IsCompleted%2A> プロパティを使用すると、操作が完了したかどうかを確認できます。  
  
## <a name="example"></a>例  
次のコンソール アプリケーションは、操作を非同期に実行して、**AdventureWorks** サンプル データベース内のデータを更新します。 この例では、実行時間の長いプロセスをエミュレートする目的で、コマンド テキストに WAITFOR ステートメントを挿入します。 通常、コマンドの実行を遅くしようとすることはありませんが、この場合は、この処理によって、非同期動作のデモが行いやすくなります。  
  
```csharp  
using System;  
using System.Data;  
using Microsoft.Data.SqlClient;  
  
class Class1  
{  
    [STAThread]  
    static void Main()  
    {  
        // The WAITFOR statement simply adds enough time to   
        // prove the asynchronous nature of the command.  
  
        string commandText =  
          "UPDATE Production.Product SET ReorderPoint = " +  
          "ReorderPoint + 1 " +  
          "WHERE ReorderPoint Is Not Null;" +  
          "WAITFOR DELAY '0:0:3';" +  
          "UPDATE Production.Product SET ReorderPoint = " +  
          "ReorderPoint - 1 " +  
          "WHERE ReorderPoint Is Not Null";  
  
        RunCommandAsynchronously(  
            commandText, GetConnectionString());  
  
        Console.WriteLine("Press Enter to continue.");  
        Console.ReadLine();  
    }  
  
    private static void RunCommandAsynchronously(  
      string commandText, string connectionString)  
    {  
        // Given command text and connection string, asynchronously  
        // execute the specified command against the connection.   
        // For this example, the code displays an indicator as it's   
        // working, verifying the asynchronous behavior.   
        using (SqlConnection connection =  
          new SqlConnection(connectionString))  
        {  
            try  
            {  
                int count = 0;  
                SqlCommand command =   
                    new SqlCommand(commandText, connection);  
                connection.Open();  
  
                IAsyncResult result =   
                    command.BeginExecuteNonQuery();  
                while (!result.IsCompleted)  
                {  
                    Console.WriteLine(  
                                    "Waiting ({0})", count++);  
                    // Wait for 1/10 second, so the counter  
                    // doesn't consume all available   
                    // resources on the main thread.  
                    System.Threading.Thread.Sleep(100);  
                }  
                Console.WriteLine(  
                    "Command complete. Affected {0} rows.",  
                command.EndExecuteNonQuery(result));  
            }  
            catch (SqlException ex)  
            {  
                Console.WriteLine("Error ({0}): {1}",   
                    ex.Number, ex.Message);  
            }  
            catch (InvalidOperationException ex)  
            {  
                Console.WriteLine("Error: {0}", ex.Message);  
            }  
            catch (Exception ex)  
            {  
                // You might want to pass these errors  
                // back out to the caller.  
                Console.WriteLine("Error: {0}", ex.Message);  
            }  
        }  
    }  
  
    private static string GetConnectionString()  
    {  
        // To avoid storing the connection string in your code,              
        // you can retrieve it from a configuration file.   
  
        // If you have not included "Asynchronous Processing=true"  
        // in the connection string, the command will not be able  
        // to execute asynchronously.  
        return "Data Source=(local);Integrated Security=SSPI;" +  
        "Initial Catalog=AdventureWorks; " +   
        "Asynchronous Processing=true";  
    }  
}  
```  
  
## <a name="next-steps"></a>次のステップ
- [非同期操作](asynchronous-operations.md)
