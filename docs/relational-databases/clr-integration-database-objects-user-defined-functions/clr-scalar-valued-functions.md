---
title: CLR スカラー値関数 |マイクロソフトドキュメント
description: スカラー値関数は、単一の値を返します。 SQL Server CLR 統合では、マネージ コードでスカラー値のユーザー定義関数を記述できます。
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
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
ms.openlocfilehash: a44187fc41409d149501c4cda7e99817be034a12
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488432"
---
# <a name="clr-scalar-valued-functions"></a>CLR スカラー値関数
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  SVF (スカラー値関数) は、文字列値、整数値、ビット値などの単一値を返します。 マネージ コードでは、任意の .NET Framework プログラミング言語を使用して、スカラ値のユーザー定義関数を作成できます。 これらの関数からは、[!INCLUDE[tsql](../../includes/tsql-md.md)] コードや他のマネージド コードにアクセスできます。 CLR 統合の利点と、マネージ コードと[!INCLUDE[tsql](../../includes/tsql-md.md)]の間での選択の利点については、「 CLR[統合の概要](../../relational-databases/clr-integration/clr-integration-overview.md)」を参照してください。  
  
## <a name="requirements-for-clr-scalar-valued-functions"></a>CLR スカラー値関数の要件  
 .NET Framework SVF は、.NET Framework アセンブリのクラスのメソッドとして実装されます。 SVF から返される入力パラメータと型は、 **varchar**、 **char**、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**行バージョン**、 **text**、 **ntext**、 **image**、 **timestamp**、**テーブル**、**カーソル**を除き、 でサポートされるスカラー データ型のいずれかです。 SVF では、実装メソッドの戻り値のデータ型が上記のいずれかの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型になるようにする必要があります。 型変換の詳細については、「 CLR[パラメーター データのマッピング](../../relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md)」を参照してください。  
  
 .NET Framework SVF を .NET Framework 言語で実装する場合は、関数に関する追加情報を含める**SqlFunction**カスタム属性を指定できます。 **SqlFunction**属性は、関数がデータにアクセスするか、またはデータを変更するかどうか、それが決定的であるかどうか、および関数が浮動小数点演算を含むかどうかを示します。  
  
 ユーザー定義スカラー値関数は、決定的関数になる場合と非決定的関数になる場合があります。 特定の入力パラメーターのセットを渡して決定的関数を呼び出すと、常に同じ結果が返されます。 一方、特定の入力パラメーターのセットを渡して非決定的関数を呼び出すと、異なる結果が返されることがあります。  
  
> [!NOTE]  
>  入力値とデータベースの状態が同じでも、関数が必ずしも常に同じ出力値を生成しない場合は、その関数を決定的関数としてマークしないでください。 完全に決定的ではない関数を決定的関数としてマークした場合、インデックス付きビューと計算列が破損する可能性があります。 関数を確定的としてマークするには **、IsDeterministic**プロパティを true に設定します。  
  
### <a name="table-valued-parameters"></a>テーブル値パラメーター  
 テーブル値パラメーター (TVP) とは、プロシージャや関数に渡されるユーザー定義のテーブル型です。TVP を使用すると、複数行のデータを効率的にサーバーに渡すことができます。 TVP の機能はパラメーター配列に似ていますが、より柔軟性が高く、[!INCLUDE[tsql](../../includes/tsql-md.md)] との統合も緊密です。 テーブル値パラメーターを使用するとパフォーマンスが向上する可能性もあります。 また、サーバーへのラウンド トリップを減らすのにも役立ちます。 スカラー パラメーターのリストを使用するなどしてサーバーに複数の要求を送信する代わりに、データを TVP としてサーバーに送信できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のプロセスで実行されているマネージド ストアド プロシージャやマネージド関数にユーザー定義のテーブル型をテーブル値パラメーターとして渡したり、戻り値として受け取ったりすることはできません。 TVP の詳細については、「[データベース エンジン&#41;&#40;テーブル値パラメーターを使用](../../relational-databases/tables/use-table-valued-parameters-database-engine.md)する 」を参照してください。  
  
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
  
 コードの最初の行は、属性にアクセスするために**Microsoft.SqlServer.Server****を参照**し、ADO.NET名前空間にアクセスします。 (この名前空間には **、.NET**Framework データ プロバイダ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が含まれています。  
  
 次に、関数は **、名前空間にある SqlFunction**カスタム**属性を受**け取ります。 このカスタム属性は、UDF (ユーザー定義関数) がサーバーのデータを読み取るときにインプロセス プロバイダーを使用するかどうかを示します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、UDF によるデータの更新、挿入、または削除を許可していません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、インプロセス プロバイダーを使用しない UDF の実行を最適化できます。 これは、**データアクセスの種類**を **[なし]** に設定することで示されます。 その次の行で、対象のメソッドは public static (Visual Basic .NET では shared) になっています。  
  
 **名前空間にある****クラス**は、既に設定されている[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスへの接続を使用して**SqlCommand**オブジェクトにアクセスできます。 ここでは使用しませんが、現在のトランザクション コンテキストは**System.Transactions**アプリケーション プログラミング インターフェイス (API) を通じても使用できます。  
  
 関数本体のコード行のほとんどは **、System.Data.SqlClient**名前空間にある型を使用するクライアント アプリケーションを作成した開発者にとって、よく知られているものに見える必要があります。  
  
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
  
 適切なコマンド テキストは **、SqlCommand**オブジェクトを初期化することによって指定されます。 前の例では、テーブル**の SalesOrderHeader**内の行数をカウントします。 次に **、cmd**オブジェクトの**ExecuteScalar**メソッドが呼び出されます。 これにより、クエリに基づいて**int**型の値が返されます。 最後に、注文数が呼び出し側に返されます。  
  
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
>  **/clr:pure**でコンパイルされた Visual C++ データベース オブジェクトは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、 での実行にはサポートされていません。 このようなデータベース オブジェクトには、スカラー値関数などがあります。  
  
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
 [CLR パラメータ データのマッピング](../../relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md)   
 [CLR 統合カスタム属性の概要](https://msdn.microsoft.com/library/ecf5c097-0972-48e2-a9c0-b695b7dd2820)   
 [ユーザー定義関数](../../relational-databases/user-defined-functions/user-defined-functions.md)   
 [CLR データベース オブジェクトからのデータ アクセス](../../relational-databases/clr-integration/data-access/data-access-from-clr-database-objects.md)  
  
  
