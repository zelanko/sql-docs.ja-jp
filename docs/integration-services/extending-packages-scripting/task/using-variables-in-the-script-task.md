---
title: "スクリプト タスクで変数の使用 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
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
- Foreach Loop containers
- Script task [Integration Services], variables
- scripts [Integration Services], variables
- Variables property
- Variable object
- SSIS Script task, variables
- variables [Integration Services], Script task
ms.assetid: 593b5961-4bfa-4ce1-9531-a251c34e89d3
caps.latest.revision: 63
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: ccfd7ce8e8f53d12dac3b021d5f62bd03947413d
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="using-variables-in-the-script-task"></a>スクリプト タスクでの変数の使用
  スクリプト タスクで変数を使用すると、パッケージ内の別のオブジェクトとデータを交換できます。 詳細については、「[Integration Services (SSIS) の変数](../../../integration-services/integration-services-ssis-variables.md)」を参照してください。  
  
 スクリプト タスクを使用して、<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A>のプロパティ、 **Dts**オブジェクトからの読み取りと書き込みに<xref:Microsoft.SqlServer.Dts.Runtime.Variable>パッケージ内のオブジェクト。  
  
> [!NOTE]  
>  <xref:Microsoft.SqlServer.Dts.Runtime.Variable.Value%2A>のプロパティ、<xref:Microsoft.SqlServer.Dts.Runtime.Variable>型のクラスは、**オブジェクト**です。 スクリプト タスクではため**Option Strict**が有効なキャストする必要が、<xref:Microsoft.SqlServer.Dts.Runtime.Variable.Value%2A>プロパティを使用するには、適切な型です。  
  
 既存の変数を追加する、<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask.ReadOnlyVariables%2A>と<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask.ReadWriteVariables%2A>で一覧表示、**スクリプト タスク エディター**カスタム スクリプトを使用できるようにします。 変数名の大文字と小文字は区別されることに注意してください。 使って両方の型の変数にアクセスする、スクリプト内で、<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A>のプロパティ、 **Dts**オブジェクト。 使用して、**値**プロパティを個別に変数を読み書きします。 スクリプト タスクは、スクリプトが変数の値を読み取ったり変更するときに、ユーザーに意識させずにロックを管理します。  
  
 <xref:Microsoft.SqlServer.Dts.Runtime.Variables.Contains%2A> プロパティによって返される <xref:Microsoft.SqlServer.Dts.Runtime.Variables> コレクションの <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> メソッドを使用すると、変数をコードで使用する前に、その変数の存在を確認できます。  
  
 使用することも、<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A>プロパティ (Dts.VariableDispenser)、スクリプト タスクで変数と連携します。 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A> を使用する場合は、コード内で、ロック セマンティクスと、変数値のデータ型のキャストの両方を処理する必要があります。 デザイン時には使用できないが、実行時にプログラムによって生成される変数を扱う必要がある場合は、<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A> プロパティではなく、<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> プロパティを使用する必要が生じる場合があります。  
  
## <a name="using-the-script-task-within-a-foreach-loop-container"></a>Foreach ループ コンテナー内でのスクリプト タスクの使用  
 Foreach ループ コンテナー内でスクリプト タスクを繰り返し実行する場合、そのスクリプトは通常、列挙子内の現在のアイテムの内容を処理する必要があります。 たとえば、Foreach File 列挙子を使用する場合、スクリプトは現在のファイル名を取得する必要があります。また、Foreach ADO 列挙子を使用する場合、スクリプトは現在のデータ行の列の内容を取得する必要があります。  
  
 変数を使用すると、Foreach ループ コンテナーとスクリプト タスク間のこうしたやり取りが可能になります。 **変数のマッピング**のページ、 **Foreach ループ エディター**変数を 1 つの列挙アイテムによって返されるデータの各項目に割り当てます。 たとえば、Foreach File 列挙子の場合は、ファイル名のみがインデックス 0 で返されるためマッピングが必要な変数は 1 つのみですが、各行の複数のデータ列を返す列挙子の場合は、スクリプト タスクで使用する各列に、個別の変数をマップする必要があります。  
  
 列挙アイテムを変数にマップした後、必要があります、マップされた変数を追加する、 **ReadOnlyVariables**プロパティを**スクリプト**のページ、**スクリプト タスク エディター**スクリプトに使用できるようにします。 フォルダーにイメージ ファイルを処理する Foreach ループ コンテナー内のスクリプト タスクの例は、次を参照してください。[スクリプト タスクによる画像の操作](../../../integration-services/extending-packages-scripting-task-examples/working-with-images-with-the-script-task.md)です。  
  
## <a name="variables-example"></a>変数の例  
 次の例では、スクリプト タスク内の変数にアクセスし、その変数を使用してパッケージ ワークフローのパスを決定する方法を示します。 サンプルは、という名前の整数変数を作成している前提としています。`CustomerCount`と`MaxRecordCount`を追加し、 **ReadOnlyVariables**内のコレクション、**スクリプト タスク エディター**です。 `CustomerCount` 変数には、インポートされる顧客レコードの数が格納されます。 この値が `MaxRecordCount` の値よりも大きい場合、スクリプト タスクから失敗が報告されます。 `MaxRecordCount` のしきい値を超過したために失敗が発生した場合、ワークフローのエラー パスには、任意の必要なクリーンアップを実装できます。  
  
 サンプルを正常にコンパイルするには、Microsoft.SqlServer.ScriptTask アセンブリへの参照を追加する必要があります。  
  
```vb  
Public Sub Main()  
  
    Dim customerCount As Integer  
    Dim maxRecordCount As Integer  
  
    If Dts.Variables.Contains("CustomerCount") = True AndAlso _  
        Dts.Variables.Contains("MaxRecordCount") = True Then  
  
        customerCount = _  
            CType(Dts.Variables("CustomerCount").Value, Integer)  
        maxRecordCount = _  
            CType(Dts.Variables("MaxRecordCount").Value, Integer)  
  
    End If  
  
    If customerCount > maxRecordCount Then  
            Dts.TaskResult = ScriptResults.Failure  
    Else  
            Dts.TaskResult = ScriptResults.Success  
    End If  
  
End Sub  
```  
  
```csharp  
using System;  
using System.Data;  
using Microsoft.SqlServer.Dts.Runtime;  
  
public class ScriptMain  
{  
  
    public void Main()  
    {  
        int customerCount;  
        int maxRecordCount;  
  
        if (Dts.Variables.Contains("CustomerCount")==true&&Dts.Variables.Contains("MaxRecordCount")==true)  
  
        {  
            customerCount = (int) Dts.Variables["CustomerCount"].Value;  
            maxRecordCount = (int) Dts.Variables["MaxRecordCount"].Value;  
  
        }  
  
        if (customerCount>maxRecordCount)  
        {  
            Dts.TaskResult = (int)ScriptResults.Failure;  
        }  
        else  
        {  
            Dts.TaskResult = (int)ScriptResults.Success;  
        }  
  
    }  
  
}  
  
```  
  
## <a name="see-also"></a>参照  
 [Integration Services & #40 です。SSIS &#41;変数](../../../integration-services/integration-services-ssis-variables.md)   
 [パッケージの変数を使用します。](http://msdn.microsoft.com/library/7742e92d-46c5-4cc4-b9a3-45b688ddb787)  
  
  

