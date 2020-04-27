---
title: CLR スカラー値関数 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
- VB
- CSharp
helpviewer_keywords:
- SVF
- scalar-valued functions
ms.assetid: 20dcf802-c27d-4722-9cd3-206b1e77bee0
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: cf5c0b6c7004f458e424e58d738cce22e97afa2b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62919588"
---
# <a name="clr-scalar-valued-functions"></a>CLR スカラー値関数
  スカラー値関数 (SVF) は、文字列値、整数値、ビット値などの単一値を返します。任意の .NET Framework プログラミング言語を使用し、マネージド コードでユーザー定義スカラー値関数を作成できます。 これらの関数からは、[!INCLUDE[tsql](../../includes/tsql-md.md)] コードや他のマネージド コードにアクセスできます。 CLR 統合の利点とマネージコードと[!INCLUDE[tsql](../../includes/tsql-md.md)]の使い分けの詳細については、「 [Clr 統合の概要](../clr-integration/clr-integration-overview.md)」を参照してください。  
  
## <a name="requirements-for-clr-scalar-valued-functions"></a>CLR スカラー値関数の要件  
 .NET Framework SVF は、.NET Framework アセンブリのクラスのメソッドとして実装されます。 SVF から[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]返される入力パラメーターと型は、でサポートされる任意のスカラーデータ型にすること`varchar`が`char`でき`rowversion`ます。ただし、、、、、、、、、また`text`はは`ntext` `image` `timestamp` `table` `cursor`除きます。 SVF では、実装メソッドの戻り値のデータ型が上記のいずれかの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型になるようにする必要があります。 型変換の詳細については、「 [CLR パラメーターデータのマッピング](../clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md)」を参照してください。  
  
 .NET Framework 言語で .NET Framework SVF を実装する場合、`SqlFunction` カスタム属性を指定し、その関数に関する詳細情報を含めることができます。 `SqlFunction` 属性は、その関数がデータへのアクセスや変更を行うかどうか、決定的関数かどうか、浮動小数点演算を必要とするかどうかなどを示します。  
  
 ユーザー定義スカラー値関数は、決定的関数になる場合と非決定的関数になる場合があります。 特定の入力パラメーターのセットを渡して決定的関数を呼び出すと、常に同じ結果が返されます。 一方、特定の入力パラメーターのセットを渡して非決定的関数を呼び出すと、異なる結果が返されることがあります。  
  
> [!NOTE]  
>  入力値とデータベースの状態が同じでも、関数が必ずしも常に同じ出力値を生成しない場合は、その関数を決定的関数としてマークしないでください。 完全に決定的ではない関数を決定的関数としてマークした場合、インデックス付きビューと計算列が破損する可能性があります。 関数を決定的関数としてマークするには、`IsDeterministic` プロパティを True に設定します。  
  
### <a name="table-valued-parameters"></a>テーブル値パラメーター  
 テーブル値パラメーター (TVP) とは、プロシージャや関数に渡されるユーザー定義のテーブル型です。TVP を使用すると、複数行のデータを効率的にサーバーに渡すことができます。 TVP の機能はパラメーター配列に似ていますが、より柔軟性が高く、[!INCLUDE[tsql](../../includes/tsql-md.md)] との統合も緊密です。 テーブル値パラメーターを使用するとパフォーマンスが向上する可能性もあります。 また、サーバーへのラウンド トリップを減らすのにも役立ちます。 スカラー パラメーターのリストを使用するなどしてサーバーに複数の要求を送信する代わりに、データを TVP としてサーバーに送信できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のプロセスで実行されているマネージド ストアド プロシージャやマネージド関数にユーザー定義のテーブル型をテーブル値パラメーターとして渡したり、戻り値として受け取ったりすることはできません。 Tvp の詳細については、「[データベースエンジン&#41;&#40;テーブル値パラメーターの使用](../tables/use-table-valued-parameters-database-engine.md)」を参照してください。  
  
## <a name="example-of-a-clr-scalar-valued-function"></a>CLR スカラー値関数の例  
 データにアクセスして整数値を返す簡単な SVF を次に示します。  
  
```csharp  
using Microsoft.SqlServer.Server;  
using System.Data.SqlClient;  
  
public class T  
{  
    [SqlFunction(DataAccess = DataAccessKind.Read)]  
    public static int ReturnOrderCount()  
    {  
        using (SqlConnection conn   
            = new SqlConnection("context connection=true"))  
        {  
            conn.Open();  
            SqlCommand cmd = new SqlCommand(  
                "SELECT COUNT(*) AS 'Order Count' FROM SalesOrderHeader", conn);  
            return (int)cmd.ExecuteScalar();  
        }  
    }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
Public Class T  
    <SqlFunction(DataAccess:=DataAccessKind.Read)> _  
    Public Shared Function ReturnOrderCount() As Integer  
        Using conn As New SqlConnection("context connection=true")  
            conn.Open()  
            Dim cmd As New SqlCommand("SELECT COUNT(*) AS 'Order Count' FROM SalesOrderHeader", conn)  
            Return CType(cmd.ExecuteScalar(), Integer)  
        End Using  
    End Function  
End Class  
```  
  
 コードの 1 行目では、属性にアクセスするために `Microsoft.SqlServer.Server` を参照し、ADO.NET 名前空間にアクセスするために `System.Data.SqlClient` (この名前空間には、.NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の `SqlClient` が含まれます) を参照しています。  
  
 次に、この関数は `SqlFunction` 名前空間の `Microsoft.SqlServer.Server` カスタム属性を受け取ります。 このカスタム属性は、UDF (ユーザー定義関数) がサーバーのデータを読み取るときにインプロセス プロバイダーを使用するかどうかを示します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、UDF によるデータの更新、挿入、または削除を許可していません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、インプロセス プロバイダーを使用しない UDF の実行を最適化できます。 これを指定するには、`DataAccessKind` を `DataAccessKind.None` に設定します。 その次の行で、対象のメソッドは public static (Visual Basic .NET では shared) になっています。  
  
 `SqlContext` 名前空間の `Microsoft.SqlServer.Server` クラスは、既に設定されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスへの接続を使用して `SqlCommand` オブジェクトにアクセスできます。 ここでは使用されていませんが、`System.Transactions` API (アプリケーション プログラミング インターフェイス) を使って現在のトランザクション コンテキストを使用することもできます。  
  
 関数の本文に記述されているコード行のほとんどは、`System.Data.SqlClient` 名前空間の型を使用しており、クライアント アプリケーションを記述したことのある開発者にとってはなじみのあるコードです。  
  
 [C#]  
  
```  
using(SqlConnection conn = new SqlConnection("context connection=true"))   
{  
   conn.Open();  
   SqlCommand cmd = new SqlCommand(  
        "SELECT COUNT(*) AS 'Order Count' FROM SalesOrderHeader", conn);  
   return (int) cmd.ExecuteScalar();  
}    
```  
  
 [Visual Basic]  
  
```  
Using conn As New SqlConnection("context connection=true")  
   conn.Open()  
   Dim cmd As New SqlCommand( _  
        "SELECT COUNT(*) AS 'Order Count' FROM SalesOrderHeader", conn)  
   Return CType(cmd.ExecuteScalar(), Integer)  
End Using  
```  
  
 `SqlCommand` オブジェクトを初期化することにより、適切なコマンド テキストが指定されます。 上の例では、テーブル `SalesOrderHeader` 内の行数をカウントしています。 次に、`ExecuteScalar` オブジェクトの `cmd` メソッドが呼び出されます。 これにより、クエリに基づいて `int` 型の値が返されます。 最後に、注文数が呼び出し側に返されます。  
  
 このコードを FirstUdf.cs というファイルに保存すると、次のようにアセンブリとしてコンパイルできます。  
  
 [C#]  
  
```  
csc.exe /t:library /out:FirstUdf.dll FirstUdf.cs   
```  
  
 [Visual Basic]  
  
```  
vbc.exe /t:library /out:FirstUdf.dll FirstUdf.vb  
```  
  
> [!NOTE]  
>  `/t:library`は、実行可能ファイルではなくライブラリを生成することを示しています。 実行可能ファイルは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] には登録できません。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、`/clr:pure` を指定してコンパイルした Visual C++ のデータベース オブジェクトは実行できません。 このようなデータベース オブジェクトには、スカラー値関数などがあります。  
  
 アセンブリと UDF を登録する [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリと呼び出しの例を次に示します。  
  
```  
CREATE ASSEMBLY FirstUdf FROM 'FirstUdf.dll';  
GO  
  
CREATE FUNCTION CountSalesOrderHeader() RETURNS INT   
AS EXTERNAL NAME FirstUdf.T.ReturnOrderCount;   
GO  
  
SELECT dbo.CountSalesOrderHeader();  
GO  
  
```  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] で公開する関数名は、対象の public static メソッドの名前と一致している必要はありません。  
  
## <a name="see-also"></a>参照  
 [CLR パラメーターデータのマッピング](../clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md)   
 [CLR 統合のカスタム属性の概要](../../database-engine/dev-guide/overview-of-clr-integration-custom-attributes.md)   
 [ユーザー定義関数](../user-defined-functions/user-defined-functions.md)   
 [CLR データベース オブジェクトからのデータ アクセス](../clr-integration/data-access/data-access-from-clr-database-objects.md)  
  
  
