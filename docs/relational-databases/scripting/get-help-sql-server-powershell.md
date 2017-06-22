---
title: "SQL Server PowerShell のヘルプの参照 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Help [PowerShell]
- Help [SQL Server], PowerShell
- PowerShell [SQL Server], help
ms.assetid: 968c316d-db83-4c24-8ea6-9f18736842f7
caps.latest.revision: 18
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ed2c615535a6886f5157be2eda71de15f54ce1f0
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="get-help-sql-server-powershell"></a>SQL Server PowerShell のヘルプの参照
  Windows PowerShell 用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロバイダーおよびコマンドレットの使用方法に関していくつかの情報源が用意されています。 これには、Windows PowerShell 環境で参照できるヘルプが含まれます。  
  
## <a name="before-you-begin"></a>はじめに  
 Windows PowerShell について学習するには、「 [Windows PowerShell ファースト ステップ ガイド](http://go.microsoft.com/fwlink/?LinkId=217083)」をご覧ください。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コマンドレットおよびプロバイダーの概要については、「 [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md)」を参照してください。  
  
### <a name="help-in-the-windows-powershell-environment"></a>Windows PowerShell 環境でのヘルプ  
 Windows PowerShell 環境でヘルプを参照するには、 **Get-Help** コマンドレットを使用します。 **Get-Help** では、Windows PowerShell 言語および Windows PowerShell で使用できるさまざまなコマンドレットやプロバイダーの基本的なヘルプが提供されます。  
  
 **Get-Help**の使用方法の詳細については、「 [ヘルプの表示: Get-Help](http://go.microsoft.com/fwlink/?LinkId=102136)」を参照してください。  
  
### <a name="sql-server-powershell-provider-help"></a>SQL Server PowerShell プロバイダーのヘルプ  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell プロバイダーは、SQLSERVER:\SQL、SQLSERVER:\DAC フォルダーなど、SQLSERVER 仮想ドライブ上のいくつかのフォルダーを実装します。 各フォルダーは、SQL Server 管理オブジェクト モデルの 1 つに関連付けられています。 SQL Server パスの各ノードに関連付けられているメソッドとプロパティを一覧表示することはできますが、PowerShell 環境でそれらのヘルプを参照することはできません。 フォルダーと、関連するプログラミング リファレンスへのリンクの表については、「 [SQL Server PowerShell Provider](../../relational-databases/scripting/sql-server-powershell-provider.md)」をご覧ください。  
  
### <a name="invoke-sqlcmd-help"></a>Invoke-Sqlcmd のヘルプ  
 **Invoke-Sqlcmd** コマンドレットは、 **sqlcmd** ユーティリティで実行できる任意のクエリまたはスクリプト ファイルを入力として受け取ります。 **Get-Help** を使用すると **Invoke-Sqlcmd** とそのパラメーターに関する情報を取得できますが、 **sqlcmd** クエリは **Get-Help** に対応していません。  
  
 *-Query* または *-QueryFromFile* の入力には以下が含まれます。  
  
-   **sqlcmd** の変数とコマンド。 これらの変数とコマンドについては、「 [sqlcmd Utility](../../tools/sqlcmd-utility.md)」の「解説」をご覧ください。  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントのいずれでもサポートされません。 [!INCLUDE[tsql](../../includes/tsql-md.md)] 言語の詳細については、「[TRANSACT-SQL リファレンス &#40;データベース エンジン&#41;](../../t-sql/transact-sql-reference-database-engine.md)」を参照してください。  
  
-   XQuery ステートメント。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でサポートされる XQuery 言語の詳細については、「[XQuery 言語リファレンス &#40;SQL Server&#41;](../../xquery/xquery-language-reference-sql-server.md)」を参照してください。  
  
## <a name="get-help-for-a-sql-server-cmdlet"></a>SQL Server コマンドレットのヘルプの参照  
 **コマンドレットのヘルプを参照するには**  
  
-   コマンドレットの名前と返されるヘルプのレベルを指定して、Get-Help を実行します。  
  
### <a name="example-cmdlet-get-help"></a>例: コマンドレット Get-Help  
 次の例は、 **Invoke-Sqlcmd**のさまざまなレベルのヘルプを返します:  
  
```  
## Get the basic help.  
Get-Help Invoke-Sqlcmd  
  
## Get the full help.  
Get-Help Invoke-Sqlcmd –Full  
  
## Get the parameter descriptions.  
Get-Help Invoke-Sqlcmd -Parameter *  
  
## Get the code examples.  
Get-Help Invoke-Sqlcmd –Examples  
  
## Get the syntax diagram.  
Get-Help Invoke-Sqlcmd –Syntax  
```  
  
## <a name="get-a-list-of-providers"></a>プロバイダーの一覧の取得  
 **アクティブ プロバイダーの一覧を取得するには**  
  
1.  プロバイダーのカテゴリを指定して、Get-Help を実行します。  
  
 Windows PowerShell でプロバイダーのヘルプを参照する方法の詳細については、「 [ドライブとプロバイダー](http://go.microsoft.com/fwlink/?LinkId=102137)」をご覧ください。  
  
### <a name="example-get-a-list-of-providers"></a>例: プロバイダーの一覧の取得  
 次のコードは、Windows PowerShell セッションで現在有効になっているプロバイダーの一覧を返します。  
  
```  
Get-Help -Category provider  
```  
  
## <a name="get-help-about-the-sql-server-provider"></a>SQL Server プロバイダーのヘルプの参照  
 **プロバイダーのヘルプを参照するには**  
  
1.  名前を SQLServer と指定して、Get-Help を実行します。  
  
### <a name="example-get-sql-server-provider-help"></a>例: SQL Server プロバイダーのヘルプの参照  
 この例は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロバイダーに関する基本的な情報を返します。  
  
```  
Get-Help SQLServer  
```  
  
## <a name="list-methods-and-properties"></a>メソッドとプロパティの一覧表示  
 **SQL Server プロバイダーのパス内のノードのメソッドとプロパティを一覧表示するには**  
  
1.  SQL Server パスのノードに CD するか、その場所を設定された変数を作成します。  
  
2.  –Type パラメーターを Methods または Properties に設定して、 **Get-Member** コマンドレットを実行する  
  
### <a name="examples-listing-methods-and-properties"></a>例: メソッドとプロパティの一覧表示  
 この例は、Databases ノードでサポートされているメソッドを一覧表示します。  
  
```  
Set-Location SQL:\MyComputer\DEFAULT\Databases  
Get-Item . | Get-Member -Type Methods  
```  
  
 この例は、SMO Table オブジェクトに設定されている変数のプロパティを一覧表示します。  
  
```  
$MyVar = New-Object Microsoft.SqlServer.Management.SMO.Table  
$MyVar | Get-Member -Type Properties  
```  
  
## <a name="see-also"></a>参照  
 [SQL Server PowerShell Provider](../../relational-databases/scripting/sql-server-powershell-provider.md)   
 [データベース エンジン コマンドレットの使用](../../relational-databases/scripting/use-the-database-engine-cmdlets.md)  
  
  
