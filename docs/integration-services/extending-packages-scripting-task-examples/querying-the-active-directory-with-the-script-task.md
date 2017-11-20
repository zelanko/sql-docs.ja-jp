---
title: "スクリプト タスクによる Active Directory のクエリ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: extending-packages-scripting-task-examples
ms.reviewer: 
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], Active Directory access
- SSIS Script task, Active Directory access
- Script task [Integration Services], examples
- Active Directory [Integration Services]
ms.assetid: a88fefbb-9ea2-4a86-b836-e71315bac68e
caps.latest.revision: 51
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: ee5a82829785e78554b105e1f3bf3bd24f05b778
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="querying-the-active-directory-with-the-script-task"></a>スクリプト タスクによる Active Directory へのクエリの実行
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージなどの企業データ処理アプリケーションでは、Active Directory に格納されている従業員の階級、役職、またはその他の特性に基づいて、個別にデータを処理する必要性が頻繁に生じます。 Active Directory は、[!INCLUDE[msCoName](../../includes/msconame-md.md)]だけでなく、ユーザーは、コンピューターやプリンターなどの他の組織の資産に関するメタデータの一元的なストアを提供する Windows ディレクトリ サービスです。 **System.DirectoryServices** Microsoft .NET Framework の名前空間では、クラスを提供するための Active Directory に格納されている情報に基づいてデータ処理を直接ワークフローを操作するためです。  
  
> [!NOTE]  
>  複数のパッケージでより簡単に再利用できるタスクを作成する場合は、このスクリプト タスク サンプルのコードを基にした、カスタム タスクの作成を検討してください。 詳細については、「 [カスタム タスクの開発](../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md)」を参照してください。  
  
## <a name="description"></a>Description  
 次の例では、従業員の電子メール アドレスを格納する `email` 変数の値に基づき、従業員の名前、役職、および電話番号を Active Directory から取得します。 パッケージ内の優先順位制約は取得された情報を使用して、たとえば、優先度の低い電子メール メッセージを送信するか、または優先度の高いページを送信するかを従業員の役職に基づいて決定できます。  
  
#### <a name="to-configure-this-script-task-example"></a>このスクリプト タスクの例を構成するには  
  
1.  `email`、`name`、および `title` という 3 つの文字列変数を作成します。 `email` 変数の値に企業の有効な電子メール アドレスを入力します。  
  
2.  **スクリプト**のページ、**スクリプト タスク エディター**、追加、`email`変数を**ReadOnlyVariables**プロパティです。  
  
3.  追加、`name`と`title`変数を**ReadWriteVariables**プロパティです。  
  
4.  スクリプト プロジェクトに参照を追加、 **System.DirectoryServices**名前空間。  
  
5.  のインスタンスにアクセスするたびに SQL Server ログインを指定する必要はありません。 コードを使用して、 **Imports**インポートするステートメント、 **DirectoryServices**名前空間。  
  
> [!NOTE]  
>  このスクリプトを正しく実行するには、組織のネットワーク上で Active Directory が使用され、この例で使用される従業員の情報が格納されている必要があります。  
  
### <a name="code"></a>コード  
  
```vb  
Public Sub Main()  
  
    Dim directory As DirectoryServices.DirectorySearcher  
    Dim result As DirectoryServices.SearchResult  
    Dim email As String  
  
    email = Dts.Variables("email").Value.ToString  
  
    Try  
        directory = New _  
            DirectoryServices.DirectorySearcher("(mail=" & email & ")")  
        result = directory.FindOne  
        Dts.Variables("name").Value = _  
            result.Properties("displayname").ToString  
        Dts.Variables("title").Value = _  
            result.Properties("title").ToString  
        Dts.TaskResult = ScriptResults.Success  
    Catch ex As Exception  
        Dts.Events.FireError(0, _  
            "Script Task Example", _  
            ex.Message & ControlChars.CrLf & ex.StackTrace, _  
            String.Empty, 0)  
        Dts.TaskResult = ScriptResults.Failure  
    End Try  
  
End Sub  
```  
  
```csharp  
public void Main()  
{  
    //  
    DirectorySearcher directory;  
    SearchResult result;  
    string email;  
  
    email = (string)Dts.Variables["email"].Value;  
  
    try  
    {  
        directory = new DirectorySearcher("(mail=" + email + ")");  
        result = directory.FindOne();  
        Dts.Variables["name"].Value = result.Properties["displayname"].ToString();  
        Dts.Variables["title"].Value = result.Properties["title"].ToString();  
        Dts.TaskResult = (int)ScriptResults.Success;  
    }  
    catch (Exception ex)  
    {  
        Dts.Events.FireError(0, "Script Task Example", ex.Message + "\n" + ex.StackTrace, String.Empty, 0);  
        Dts.TaskResult = (int)ScriptResults.Failure;  
    }  
  
}  
```  
  
## <a name="external-resources"></a>外部リソース  
  
-   技術記事「 [SSIS での Active Directory 情報の処理](http://go.microsoft.com/fwlink/?LinkId=199588)、social.technet.microsoft.com  
  
  

