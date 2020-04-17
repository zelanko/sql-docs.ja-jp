---
title: オブジェクト |マイクロソフトドキュメント
description: ユーザー接続で SQL Server のマネージ コードを呼び出すと、呼び出し元のコンテキストへのアクセスは SqlContext オブジェクトで抽象化されます。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- Windows identity [CLR integration]
- SqlContext object
- context [CLR integration]
ms.assetid: 67437853-8a55-44d9-9337-90689ebba730
author: rothja
ms.author: jroth
ms.openlocfilehash: cd6d3091b155ae829e368bdd182b3da8286c7194
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487541"
---
# <a name="sqlcontext-object"></a>SqlContext オブジェクト
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  プロシージャや関数の呼び出し時、CLR (共通言語ランタイム) ユーザー定義型のメソッドの呼び出し時、または任意の [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework 言語で定義されたトリガーの起動時には、サーバーのマネージド コードを呼び出します。 このコードの実行はユーザー接続の一環として要求されるので、サーバーで実行しているコードから呼び出し元のコンテキストにアクセスできる必要があります。 また、特定のデータ アクセス操作には、コードが呼び出し元のコンテキストで実行されている場合にしか有効にならないものもあります。 たとえば、トリガー操作で使用される inserted 擬似テーブルや deleted 擬似テーブルにアクセスするには、コードが呼び出し元のコンテキストで実行されている必要があります。  
  
 呼び出し元のコンテキストは **、SqlContext**オブジェクトで抽象化されます。 **メソッドと**プロパティの詳細については、SDK**のクラス**リファレンス ドキュメントを[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]参照してください。  
  
 **SqlContext は**、次のコンポーネントへのアクセスを提供します。  
  
-   **SqlPipe**: **SqlPipe**オブジェクトは、結果がクライアントに流れる "パイプ" を表します。 **オブジェクト**の詳細については、「 [SqlPipe オブジェクト](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqlpipe-object.md)」を参照してください。  
  
-   **SQL トリガー コンテキスト**: CLR**トリガー**内からのみ取得できます。 このオブジェクトでは、トリガーを起動した操作や、更新された列のマップについての情報を提供します。 オブジェクトの詳細については **、「SqlTriggerContext**オブジェクト」を参照[してください](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqltriggercontext-object.md)。  
  
-   **IsAvailable**: **IsAvailable**プロパティは、コンテキストの可用性を判断するために使用されます。  
  
-   **WindowsId**: **WindowsId**プロパティは、呼び出し元の Windows ID を取得するために使用されます。  
  
## <a name="determining-context-availability"></a>コンテキスト可用性の判断  
 現在実行中のコードがインプロセスで実行されているかどうかを調めるには **、SqlContext**クラスを照会します。 これを行うには **、SqlContext**オブジェクトの**IsAvailable**プロパティを確認します。 **IsAvailable**プロパティは読み取り専用で**True**、呼び出し元のコード[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が内部で実行されている場合、および他の**SqlContext**メンバーにアクセスできる場合は True を返します。 **プロパティ**が**False を**返す場合、他のすべての**SqlContext**メンバーは**無効なオペレーション例外**をスローします。 **IsAvailable が** **False**を返す場合、接続文字列に "コンテキスト接続=true" が含まれる接続オブジェクトを開こうとすると、そのオブジェクトを開こうとすると、エラーが発生します。  
  
## <a name="retrieving-windows-identity"></a>Windows ID の取得  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内で実行されている CLR コードは、常に、プロセス アカウントのコンテキストで呼び出されます。 コードがプロセス ID ではなく、呼び出し元のユーザーの ID[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を使用して特定のアクションを実行する必要がある場合は、偽装トークンを取得する必要があります、 **SqlContext**オブジェクトの**WindowsIdentity**プロパティです。 **WindowsIdentity**プロパティは、呼び出し元の[!INCLUDE[msCoName](../../includes/msconame-md.md)]Windows ID を表す**WindowsId**インスタンスを返[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 このプロパティには **、EXTERNAL_ACCESS**または**UNSAFE**アクセス許可が設定されているアセンブリのみがアクセスできます。  
  
 **WindowsIdentity**オブジェクトを取得した後、呼び出し元はクライアント アカウントを偽装し、クライアントアカウントに代わってアクションを実行できます。  
  
 呼び出し元の ID は、Windows 認証を使用してサーバーに接続されたストアド プロシージャまたは関数の実行を開始したクライアントの場合にのみ **、SqlContext.WindowsIdentity**を介して使用できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証が使用されている場合、このプロパティは NULL になり、コードでは呼び出し元ユーザーの権限を借用することはできません。  
  
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
 [オブジェクト](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqlpipe-object.md)   
 [オブジェクト](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqltriggercontext-object.md)   
 [CLR トリガー](https://msdn.microsoft.com/library/302a4e4a-3172-42b6-9cc0-4a971ab49c1c)   
 [ADO.NET に対する SQL Server インプロセス固有の拡張機能](../../relational-databases/clr-integration-data-access-in-process-ado-net/sql-server-in-process-specific-extensions-to-ado-net.md)  
  
  
