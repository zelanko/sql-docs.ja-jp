---
title: "スクリプト タスク内のデータ ソースへの接続 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: extending-packages-scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- connections [Integration Services], scripts
- Integration Services packages, connections
- connection managers [Integration Services], scripts
- scripts [Integration Services], connections
- SSIS packages, connections
- packages [Integration Services], connections
- Script task [Integration Services], connections
- Connections property
- SQL Server Integration Services packages, connections
- SSIS Script task, connections
ms.assetid: 9c008380-715b-455b-9da7-22572d67c388
caps.latest.revision: 59
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 825ff059476614085a338dd9c568031885bed64b
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="connecting-to-data-sources-in-the-script-task"></a>スクリプト タスクでのデータ ソースへの接続
  接続マネージャーは、パッケージ内に構成されたデータ ソースへのアクセスを提供します。 詳細については、「[Integration Services &#40;SSIS&#41; の接続](../../../integration-services/connection-manager/integration-services-ssis-connections.md)」を参照してください。  
  
 スクリプト タスクがを介してこれらの接続マネージャーにアクセスできる、<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A>のプロパティ、 **Dts**オブジェクト。 <xref:Microsoft.SqlServer.Dts.Runtime.Connections> コレクション内の各接続マネージャーは、基になるデータ ソースへの接続方法に関する情報を格納しています。  
  
 接続マネージャーの <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> メソッドを呼び出すと、その接続マネージャーがまだ接続されていない場合、データ ソースに接続され、ユーザーのスクリプト タスク コードで使用する適切な接続または接続情報が返されます。  
  
> [!NOTE]  
>  呼び出しの前に、接続マネージャーによって返される接続の種類を知る必要があります**AcquireConnection**です。 スクリプト タスクではため**Option Strict**が有効な型として返されると、接続をキャストする必要があります**オブジェクト**、使用する前に適切な接続の種類にします。  
  
 <xref:Microsoft.SqlServer.Dts.Runtime.Connections.Contains%2A> プロパティによって返される <xref:Microsoft.SqlServer.Dts.Runtime.Connections> コレクションの <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A> メソッドを使用すると、既存の接続をコードで使用する前に検索できます。  
  
> [!IMPORTANT]  
>  スクリプト タスクのマネージ コードで、OLE DB 接続マネージャーや Excel 接続マネージャーなど、アンマネージ オブジェクトを返す接続マネージャーの AcquireConnection メソッドを呼び出すことはできません。 ただし、これらの接続マネージャーの ConnectionString プロパティを読み取るし、接続文字列を使用して、コード内で直接データ ソースへの接続、 **OledbConnection**から、 **System.Data.OleDb**名前空間。  
>   
>  アンマネージ オブジェクトを返すマネージャーの接続の AcquireConnection メソッドを呼び出す必要があります場合、を使用して、[!INCLUDE[vstecado](../../../includes/vstecado-md.md)]接続マネージャーです。 OLE DB プロバイダーを使用するように [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] 接続マネージャーを構成すると、接続には [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Data Provider for OLE DB が使用されます。 この場合、AcquireConnection メソッドを返します、 **system.data.oledb.oledbconnection で**アンマネージ オブジェクトの代わりにします。 構成する、 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] 、Excel のデータ ソースを選択で使用する接続マネージャー、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] OLE DB Provider for Jet は、Excel ファイルを指定し、入力`Excel 8.0`(Excel 97 以降) の値として**拡張プロパティ**上、**すべて**のページ、**接続マネージャー**  ダイアログ ボックス。  
  
## <a name="connections-example"></a>接続の使用例  
 次の例では、スクリプト タスク内での接続マネージャーへのアクセス方法を示します。 このサンプルでは、作成、構成したことが前提としています、[!INCLUDE[vstecado](../../../includes/vstecado-md.md)]接続マネージャーの名前付き**Test ADO.NET Connection**とフラット ファイル接続マネージャーの名前付き**Test Flat File Connection**です。 なお、[!INCLUDE[vstecado](../../../includes/vstecado-md.md)]接続マネージャーを返します、 **SqlConnection**すぐに、データ ソースへの接続に使用できるオブジェクト。 フラット ファイル接続マネージャーは、その一方で、パスとファイル名を含む文字列だけを返します。 メソッドを使用する必要があります、 **System.IO**名前空間を開くし、フラット ファイルを使用します。  
  
```vb  
Public Sub Main()  
  
    Dim myADONETConnection As SqlClient.SqlConnection  
    myADONETConnection = _  
        DirectCast(Dts.Connections("Test ADO.NET Connection").AcquireConnection(Dts.Transaction), _  
        SqlClient.SqlConnection)  
    MsgBox(myADONETConnection.ConnectionString, _  
        MsgBoxStyle.Information, "ADO.NET Connection")  
  
    Dim myFlatFileConnection As String  
    myFlatFileConnection = _  
        DirectCast(Dts.Connections("Test Flat File Connection").AcquireConnection(Dts.Transaction), _  
        String)  
    MsgBox(myFlatFileConnection, MsgBoxStyle.Information, "Flat File Connection")  
  
    Dts.TaskResult = ScriptResults.Success  
  
End Sub  
```  
  
```csharp  
using System;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Dts.Runtime;  
using System.Windows.Forms;  
  
public class ScriptMain  
{  
  
        public void Main()  
        {  
            SqlConnection myADONETConnection = new SqlConnection();  
            myADONETConnection = (SqlConnection)(Dts.Connections["Test ADO.NET Connection"].AcquireConnection(Dts.Transaction)as SqlConnection);  
            MessageBox.Show(myADONETConnection.ConnectionString, "ADO.NET Connection");  
  
            string myFlatFileConnection;  
            myFlatFileConnection = (string)(Dts.Connections["Test Flat File Connection"].AcquireConnection(Dts.Transaction) as String);  
            MessageBox.Show(myFlatFileConnection, "Flat File Connection");  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
  
}  
  
```  
  
## <a name="see-also"></a>参照  
 [Integration Services &#40;SSIS&#41; の接続](../../../integration-services/connection-manager/integration-services-ssis-connections.md)   
 [接続マネージャーを作成します。](http://msdn.microsoft.com/library/6ca317b8-0061-4d9d-b830-ee8c21268345)  
  
  

