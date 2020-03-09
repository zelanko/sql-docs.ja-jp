---
title: SQL Server のインスタンスの列挙 (ADO.NET)
description: SQL Server のアクティブなインスタンスを一覧化する方法について説明します。
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: ddf1c83c-9d40-45e6-b04d-9828c6cbbfdc
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: bd0dbbedcb2fa33af80e0a1a1d593bf7df27edb6
ms.sourcegitcommit: 610e49c3e1fa97056611a85e31e06ab30fd866b1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/07/2020
ms.locfileid: "78896955"
---
# <a name="enumerating-instances-of-sql-server-adonet"></a>SQL Server のインスタンスの列挙 (ADO.NET)

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

SQL Server では、アプリケーションが現在のネットワーク内の SQL Server インスタンスを検索できます。 <xref:System.Data.Sql.SqlDataSourceEnumerator> クラスは、この情報をアプリケーション開発者に公開し、表示されるすべてのサーバーに関する情報を含む <xref:System.Data.DataTable> を提供します。 このときに返されるテーブルには、ユーザーが新しい接続を作成しようとして、 **[接続プロパティ]** ダイアログ ボックスで、利用可能なすべてのサーバーが含まれたドロップダウン リストを展開したときに表示されるリストと一致するサーバー インスタンスのリストが含まれています。 表示される結果が完全なものであるとは限りません。  
  
> [!NOTE]
>  ほとんどの Windows サービスと同様に、SQL Browser サービスは必要最小限の特権で実行することをお勧めします。 SQL Browser サービスの詳細および SQL Browser サービスの動作を管理する方法については、SQL Server オンライン ブックを参照してください。  
  
## <a name="retrieving-an-enumerator-instance"></a>列挙子インスタンスの取得  
使用可能な SQL Server インスタンスに関する情報を含むテーブルを取得するには、まず、共有プロパティまたは静的プロパティである <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> プロパティを使用して列挙子を取得する必要があります。  
  
```csharp  
System.Data.Sql.SqlDataSourceEnumerator instance =   
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
静的インスタンスを取得したら、使用可能なサーバーに関する情報を含む <xref:System.Data.DataTable> を返す <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> メソッドを呼び出すことができます。  
  
```csharp  
System.Data.DataTable dataTable = instance.GetDataSources();  
```  
  
このメソッド呼び出しから返されるテーブルには次の列が含まれ、そのすべてに `string` 値が含まれています。  
  
|列|説明|  
|------------|-----------------|  
|**ServerName**|サーバー名。|  
|**InstanceName**|サーバー インスタンスの名前。 サーバーが既定のインスタンスとして実行されている場合は空白です。|  
|**IsClustered**|サーバーがクラスターの一部であるかどうかを示します。|  
|**Version**|サーバーのバージョン。 次に例を示します。<br /><br /> -   9.00.x (SQL Server 2005)<br />-10.0.xx (SQL Server 2008)<br />-   10.50.x (SQL Server 2008 R2)<br />-11.0.xx (SQL Server 2012)|  
  
## <a name="enumeration-limitations"></a>列挙の制限  
使用可能なすべてのサーバーが一覧表示されるとは限りません。 この一覧は、タイムアウトやネットワーク トラフィックなどの要因によって異なることがあります。 このため、2 回の連続呼び出しで一覧が異なる場合があります。 同じネットワーク上のサーバーのみが一覧表示されます。 ブロードキャスト パケットは通常、ルーターをスキャンしません。あるサーバーが一覧表示されないことがあっても、複数の呼び出し間で安定しているのはこのためです。  
  
一覧表示されたサーバーに、常に `IsClustered` やバージョンなどの追加情報があるとは限りません。 これは、その一覧がどのように取得されたかによって異なります。 SQL Server Browser サービスを介して一覧に表示されるサーバーには、一覧に名前しか表示されない、Windows インフラストラクチャを介して検索されたサーバーより多くの詳細情報が含まれています。  
  
> [!NOTE]
>  サーバーの列挙は、完全に信頼され、実行されている場合にのみ使用できます。 部分的に信頼された環境で実行されているアセンブリは、<xref:Microsoft.Data.SqlClient.SqlClientPermission> コード アクセス セキュリティ (CAS) アクセス許可がある場合でも使用できません。  
  
SQL Server では、SQL Browser という名前の外部の Windows サービスを利用して、<xref:System.Data.Sql.SqlDataSourceEnumerator> に情報を提供します。 このサービスは既定で有効になっていますが、管理者はそれをオフにするか、無効にして、サーバー インスタンスをこのクラスに表示しないようにすることができます。  
  
## <a name="example"></a>例  
次のコンソール アプリケーションは、表示可能なすべての SQL Server インスタンスに関する情報を取得し、その情報をコンソール ウィンドウに表示します。  
  
```csharp  
using System.Data.Sql;  
  
class Program  
{  
  static void Main()  
  {  
    // Retrieve the enumerator instance and then the data.  
    SqlDataSourceEnumerator instance =  
      SqlDataSourceEnumerator.Instance;  
    System.Data.DataTable table = instance.GetDataSources();  
  
    // Display the contents of the table.  
    DisplayData(table);  
  
    Console.WriteLine("Press any key to continue.");  
    Console.ReadKey();  
  }  
  
  private static void DisplayData(System.Data.DataTable table)  
  {  
    foreach (System.Data.DataRow row in table.Rows)  
    {  
      foreach (System.Data.DataColumn col in table.Columns)  
      {  
        Console.WriteLine("{0} = {1}", col.ColumnName, row[col]);  
      }  
      Console.WriteLine("============================");  
    }  
  }  
}  
```  
  
## <a name="next-steps"></a>次のステップ
- [SQL Server と ADO.NET](index.md)
