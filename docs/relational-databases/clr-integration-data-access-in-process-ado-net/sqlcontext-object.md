---
title: "SqlContext オブジェクト |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- Windows identity [CLR integration]
- SqlContext object
- context [CLR integration]
ms.assetid: 67437853-8a55-44d9-9337-90689ebba730
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 627620311feafae43e41c23b65552c3f1d2f612c
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="sqlcontext-object"></a>SqlContext オブジェクト
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
プロシージャや関数の呼び出し時、CLR (共通言語ランタイム) ユーザー定義型のメソッドの呼び出し時、または任意の [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework 言語で定義されたトリガーの起動時には、サーバーのマネージ コードを呼び出します。 このコードの実行はユーザー接続の一環として要求されるので、サーバーで実行しているコードから呼び出し元のコンテキストにアクセスできる必要があります。 また、特定のデータ アクセス操作には、コードが呼び出し元のコンテキストで実行されている場合にしか有効にならないものもあります。 たとえば、トリガー操作で使用される inserted 擬似テーブルや deleted 擬似テーブルにアクセスするには、コードが呼び出し元のコンテキストで実行されている必要があります。  
  
 呼び出し元のコンテキストが抽象化されて、 **SqlContext**オブジェクト。 詳細については、 **SqlTriggerContext**メソッドとプロパティを参照してください、 **Microsoft.SqlServer.Server.SqlTriggerContext**クラスのリファレンス ドキュメントで、 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK。  
  
 **SqlContext**次のコンポーネントへのアクセスを提供します。  
  
-   **SqlPipe**: **SqlPipe**オブジェクトを介して結果をクライアントに送信「パイプ」を表します。 詳細については、 **SqlPipe**オブジェクトを参照してください[SqlPipe オブジェクト](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqlpipe-object.md)です。  
  
-   **SqlTriggerContext**: **SqlTriggerContext** CLR トリガー内からオブジェクトが取得のみできます。 このオブジェクトでは、トリガーを起動した操作や、更新された列のマップについての情報を提供します。 詳細については、 **SqlTriggerContext**オブジェクトを参照してください[SqlTriggerContext オブジェクト](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqltriggercontext-object.md)です。  
  
-   **IsAvailable**: **IsAvailable**プロパティはコンテキスト可用性を判断するために使用します。  
  
-   **WindowsIdentity**: **WindowsIdentity**プロパティは、呼び出し元の Windows id を取得するために使用します。  
  
## <a name="determining-context-availability"></a>コンテキスト可用性の判断  
 クエリ、 **SqlContext**クラスから実行中のコードがインプロセスで実行しているかどうか。 これを行うには、確認、 **IsAvailable**のプロパティ、 **SqlContext**オブジェクト。 **IsAvailable**プロパティは読み取り専用、および返します**True**の内部呼び出し元のコードが実行されている場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]他の場合と**SqlContext**メンバーにアクセスできます。 場合、 **IsAvailable**プロパティから返される**False**、他のすべて**SqlContext**メンバーをスロー、 **InvalidOperationException**使用されている場合、. 場合**IsAvailable**を返します**False**、開いている接続オブジェクトを呼び出そうとすると"コンテキスト接続 = true"では、接続文字列が失敗します。  
  
## <a name="retrieving-windows-identity"></a>Windows ID の取得  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内で実行されている CLR コードは、常に、プロセス アカウントのコンテキストで呼び出されます。 場合は、コードの代わりに、呼び出しユーザーの id を使用して特定のアクションを実行する必要があります、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を通じての権限借用トークンを取得するか、プロセス id で、 **WindowsIdentity** のプロパティ**SqlContext**オブジェクト。 **WindowsIdentity**プロパティから返される、 **WindowsIdentity**インスタンスを表す、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 、呼び出し元、または null を使用して、クライアントが認証された場合の Windows id [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。 マークされたアセンブリだけ**EXTERNAL_ACCESS**または**UNSAFE**アクセス許可がこのプロパティにアクセスできます。  
  
 取得した後に、 **WindowsIdentity**オブジェクト、呼び出し元がクライアントのアカウントを借用して、ユーザーに代わってに対してアクションを実行します。  
  
 呼び出し元の id はのみで使用**SqlContext.WindowsIdentity**ストアド プロシージャまたは関数の実行を開始したクライアントが Windows 認証を使用して、サーバーに接続されているかどうか。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証が使用されている場合、このプロパティは NULL になり、コードでは呼び出し元ユーザーの権限を借用することはできません。  
  
### <a name="example"></a>例  
 次の例では、呼び出し元であるクライアントの Windows ID を取得し、クライアントの権限を借用する方法を示します。  
  
 C#  
  
```  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void WindowsIDTestProc()  
{  
    WindowsIdentity clientId = null;  
    WindowsImpersonationContext impersonatedUser = null;  
  
    // Get the client ID.  
    clientId = SqlContext.WindowsIdentity;  
  
    // This outer try block is used to thwart exception filter   
    // attacks which would prevent the inner finally   
    // block from executing and resetting the impersonation.  
    try  
    {  
        try  
        {  
            impersonatedUser = clientId.Impersonate();  
            if (impersonatedUser != null)  
            {  
                // Perform some action using impersonation.  
            }  
        }  
        finally  
        {  
            // Undo impersonation.  
            if (impersonatedUser != null)  
                impersonatedUser.Undo();  
        }  
    }  
    catch  
    {  
        throw;  
    }  
}  
```  
  
 Visual Basic  
  
```  
<Microsoft.SqlServer.Server.SqlProcedure()> _  
Public Shared Sub  WindowsIDTestProcVB ()  
    Dim clientId As WindowsIdentity  
    Dim impersonatedUser As WindowsImpersonationContext  
  
    ' Get the client ID.  
    clientId = SqlContext.WindowsIdentity  
  
    ' This outer try block is used to thwart exception filter   
    ' attacks which would prevent the inner finally   
    ' block from executing and resetting the impersonation.  
  
    Try  
        Try  
  
            impersonatedUser = clientId.Impersonate()  
  
            If impersonatedUser IsNot Nothing Then  
                ' Perform some action using impersonation.  
            End If  
  
        Finally  
            ' Undo impersonation.  
            If impersonatedUser IsNot Nothing Then  
                impersonatedUser.Undo()  
            End If  
        End Try  
  
    Catch e As Exception  
  
        Throw e  
  
    End Try  
End Sub  
```  
  
## <a name="see-also"></a>参照  
 [SqlPipe オブジェクト](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqlpipe-object.md)   
 [SqlTriggerContext オブジェクト](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqltriggercontext-object.md)   
 [CLR トリガー](http://msdn.microsoft.com/library/302a4e4a-3172-42b6-9cc0-4a971ab49c1c)   
 [ADO.NET に対する SQL Server インプロセス固有の拡張機能](../../relational-databases/clr-integration-data-access-in-process-ado-net/sql-server-in-process-specific-extensions-to-ado-net.md)  
  
  
