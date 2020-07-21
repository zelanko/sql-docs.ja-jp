---
title: CLR データベースオブジェクトのデバッグ |Microsoft Docs
description: SQL Server は、SQL Server デバッガーと Microsoft Visual Studio デバッガーを統合するデータベース内の Transact-sql オブジェクトと CLR オブジェクトのデバッグをサポートします。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- database objects [CLR integration], debugging
- permissions [CLR integration]
- debugging [CLR integration]
- building database objects [CLR integration], debugging
- common language runtime [SQL Server], debugging
ms.assetid: 1332035c-d6ed-424d-8234-46ad21168319
author: rothja
ms.author: jroth
ms.openlocfilehash: 7af58a109a658a4af60ca49ad6eea401284782ac
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85756316"
---
# <a name="debugging-clr-database-objects"></a>CLR データベース オブジェクトのデバッグ
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、データベース内の [!INCLUDE[tsql](../../includes/tsql-md.md)] オブジェクトと CLR (共通言語ランタイム) オブジェクトのデバッグがサポートされます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でのデバッグの重要な特徴は、セットアップと使用が容易になったことと、SQL Server デバッガーと Microsoft Visual Studio デバッガーが統合されたことです。 さらに、複数の言語にまたがったデバッグを実行できます。 ユーザーは [!INCLUDE[tsql](../../includes/tsql-md.md)] から CLR オブジェクト (またはその逆) にシームレスにステップインできます。 SQL Server Management Studio の Transact-SQL デバッガーを使用してマネージド データベース オブジェクトをデバッグすることはできませんが、Visual Studio のデバッガーを使用すると、このオブジェクトをデバッグすることができます。 Visual Studio でのマネージド データベース オブジェクトのデバッグでは、サーバーで実行するルーチン内の "step into" ステートメントや "step over" ステートメントなど、一般的なデバッグ機能すべてがサポートされます。 デバッグ中は、ブレークポイントの設定、呼び出し履歴の調査、変数の調査、変数値の変更を行うことができます。 Visual Studio .NET 2003 は、CLR 統合プログラミングまたはデバッグには使用できない点に注意してください。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] には .NET Framework がプレインストールされていますが、Visual Studio .NET 2003 では .NET Framework 2.0 アセンブリを使用できません。  
  
 Visual Studio を使用したマネージコードのデバッグの詳細については、Visual Studio ドキュメントの「[マネージコードのデバッグ](https://go.microsoft.com/fwlink/?LinkId=120377)」を参照してください。  
  
## <a name="debugging-permissions-and-restrictions"></a>デバッグに関する権限と制限事項  
 デバッグは高度な権限を持つ操作であるため、では**sysadmin**固定サーバーロールのメンバーだけがこの操作を実行でき [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
 デバッグ中には、次の制限事項が適用されます。  
  
-   CLR ルーチンを同時にデバッグできるデバッガー インスタンスは 1 つに制限されます。 この制限が適用されるのは、ブレークポイントに到達するとすべての CLR コードの実行が停止し、デバッガーがブレークポイントから先に動作を進めるまで、コードの実行を再開できないことが理由です。 ただし、他の接続での [!INCLUDE[tsql](../../includes/tsql-md.md)] のデバッグは続行できます。 [!INCLUDE[tsql](../../includes/tsql-md.md)] デバッグによりサーバーの他の実行が停止することはありませんが、デバッグがロックをかけると、他の接続が待機することになる場合があります。  
  
-   デバッグできるのは、既存の接続ではなく新しい接続のみです。これは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が、接続が行われる前のクライアントとデバッガーの環境に関する情報を必要とするためです。  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] コードと CLR コードのデバッグは、上記の制限事項により、実稼働サーバーではなくテスト サーバーで行うことをお勧めします。  
  
## <a name="overview-of-debugging-managed-database-objects"></a>マネージド データベース オブジェクトのデバッグの概要  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデバッグは、接続ごとのモデルに準拠します。 デバッガーは、デバッガーがアタッチされているクライアント接続のみに関係したアクティビティを検出してデバッグを実行することができます。 デバッガーの機能は、接続の種類による制限を受けないので、表形式のデータ ストリーム (TDS) 接続と HTTP 接続の両方をデバッグできます。 ただし、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、既存の接続をデバッグできません。 デバッグでは、サーバーで実行するルーチン内のすべての一般的なデバッグ機能をサポートします。 デバッガーと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] との間のやり取りは、分散 COM (コンポーネント オブジェクト モデル) 経由で行われます。  
  
 マネージストアドプロシージャ、関数、トリガー、ユーザー定義型、および集計のデバッグの詳細およびシナリオについては、Visual Studio ドキュメントの「[SQL SERVER CLR Integration Database デバッグ](https://go.microsoft.com/fwlink/?LinkId=120378)」を参照してください。  
  
 Visual Studio を使用してリモートで開発およびデバッグを行うには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスで TCP/IP ネットワーク プロトコルを有効にする必要があります。 サーバーで TCP/IP プロトコルを有効にする方法の詳細については、「[クライアントプロトコルを構成する](../../database-engine/configure-windows/configure-client-protocols.md)」を参照してください。  
  
#### <a name="to-debug-a-managed-database-object"></a>マネージド データベース オブジェクトをデバッグするには  
  
1.  Microsoft Visual Studio を開き、新しい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロジェクトを作成して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスでデータベースへの接続を確立します。  
  
2.  新しい型を作成します。 **ソリューションエクスプローラー**で、プロジェクトを右クリックし、[**追加**]、[**新しい項目...** ] の順に選択します。[**新しい項目の追加**] ウィンドウで、[**ストアドプロシージャ**]、[**ユーザー定義関数**]、[**ユーザー定義型**]、[**トリガー**]、[**集計**]、または [**クラス**] を選択します。 新しい種類のソースファイルの名前を指定し、[**追加**] をクリックします。  
  
3.  テキスト エディターに新しい型のコードを追加します。 ストアド プロシージャの例のサンプル コードについては、後のセクションを参照してください。  
  
4.  型をテストするスクリプトを追加します。 **ソリューションエクスプローラー**で、[ **TestScripts** ] ディレクトリを展開し、[ **test .sql** ] をダブルクリックして、既定のテストスクリプトソースファイルを開きます。 デバッグするコードを呼び出すテスト スクリプトをテキスト エディターに追加します。 サンプル スクリプトについては、下記を参照してください。  
  
5.  ソース コードに 1 つ以上のブレークポイントを配置します。 テキストエディターで、デバッグする関数またはルーチン内のコード行を右クリックし、[**ブレークポイント**] と [**ブレークポイントの挿入**] を選択します。 ブレークポイントが追加され、コード行が赤で強調表示されます。  
  
6.  [**デバッグ**] メニューの [**デバッグ開始**] をクリックして、プロジェクトをコンパイル、配置、およびテストします。 Test.sql のテスト スクリプトが実行され、マネージド データベース オブジェクトが呼び出されます。  
  
7.  命令ポインターを表す黄色い矢印がブレークポイントに表示されると、コードの実行が一時停止され、マネージド データベース オブジェクトのデバッグを開始できます。 [**デバッグ**] メニューから**ステップオーバー**して、命令ポインターを次のコード行に進めることができます。 [**ローカル**] ウィンドウは、命令ポインターで現在強調表示されているオブジェクトの状態を確認するために使用されます。 変数は [**ウォッチ**] ウィンドウに追加できます。 監視される変数の状態は、変数が命令ポインターにより現在強調表示されているコード行にあるときだけでなく、デバッグ セッション全体で見ることができます。 [デバッグ] メニューの [続行] をクリックし、命令ポインターを次のブレークポイントに進めるか、ブレークポイントがこれ以上ない場合にはルーチンの実行を完了します。  
  
### <a name="example"></a>例  
 次の例では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョンを呼び出し元に返します。  
  
 C#  
  
```  
using System;  
using System.Data;  
using System.Data.SqlTypes;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
  
public class StoredProcedures   
{  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void GetVersion()  
   {  
   using(SqlConnection connection = new SqlConnection("context connection=true"))   
   {  
      connection.Open();  
      SqlCommand command = new SqlCommand("select @@version",  
                                           connection);  
      SqlContext.Pipe.ExecuteAndSend(command);  
      }  
   }  
}  
```  
  
 Visual Basic  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
Partial Public Class StoredProcedures   
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub GetVersion()  
        Using connection As New SqlConnection("context connection=true")  
            connection.Open()  
            Dim command As New SqlCommand("SELECT @@VERSION", connection)  
            SqlContext.Pipe.ExecuteAndSend(command)  
        End Using  
    End Sub  
End Class  
```  
  
 上で定義した GetVersion ストアド プロシージャを呼び出すテスト スクリプトを次に示します。  
  
```  
EXEC GetVersion  
```  
  
## <a name="see-also"></a>関連項目  
 [CLR &#40;共通言語ランタイム&#41; 統合のプログラミング概念](../../relational-databases/clr-integration/common-language-runtime-clr-integration-programming-concepts.md)  
  
  
