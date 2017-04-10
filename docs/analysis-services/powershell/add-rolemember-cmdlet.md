---
title: "Add-RoleMember コマンドレット | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 827c8bbc-d48f-4e49-9ea5-abb1380f7623
caps.latest.revision: 14
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 14
---
# Add-RoleMember コマンドレット
  Analysis Services のテーブル データベースまたは多次元データベースの特定のロールにメンバーを追加します。  
  
## 構文  
 `Add-RoleMember [-MemberName] <System.String> [-Database] <System.String> [-RoleName] <System.String> [<CommonParameters>]`  
  
 `Add-RoleMember [-MemberName] <System.String> [-DatabaseRole] <Microsoft.AnalysisServices.Role> [<CommonParameters>]`  
  
## Description  
 Add-RoleMember コマンドレットは、既存のデータベース ロールに有効なメンバーを追加します。 データベース ロールのみが許可されます。 このコマンドレットを使用して、サーバー ロールにメンバーを追加することはできません。  
  
 一度に追加できるのは 1 つのメンバーのみで、ユーザー アカウントまたはグループ アカウントです。  
  
## パラメーター  
  
### -MemberName \<string>  
 ロールに追加する Windows ユーザーまたはグループを指定します。  
  
|||  
|-|-|  
|必須/省略可能|true|  
|位置|0|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### -Database \<string>  
 ロールが属するデータベースを指定します。  
  
|||  
|-|-|  
|必須/省略可能|true|  
|位置|1|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### -RoleName \<string>  
 メンバーの追加先となるロールを指定します。  
  
|||  
|-|-|  
|必須/省略可能|true|  
|位置|2|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### -DatabaseRole \<string>  
 メンバーの追加先となる Microsoft.AnalysisServices.Role オブジェクトを指定します。 データベース ロールをパイプラインを介して指定する場合に、–Database および –RoleName パラメーターの代わりにこのパラメーターを使用します。  
  
|||  
|-|-|  
|必須/省略可能|true|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|可 (ByPropertyName)|  
|ワイルドカード文字の受け入れ|オプション|  
  
### \<CommonParameters>  
 このコマンドレットは、-Verbose、-Debug、-ErrorAction、-ErrorVariable、-OutBuffer、および –OutVariable の共通パラメーターをサポートしています。 詳細については、「[About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825)」を参照してください。  
  
## 入力および出力  
 入力型は、コマンドレットにパイプできるオブジェクトの型です。 戻り値の型は、コマンドレットが返すオブジェクトの型です。  
  
|||  
|-|-|  
|入力|[なし] :|  
|出力|なし|  
  
## 例 1  
  
```  
PS SQLSERVER:\sqlas\localhost\default> add-rolemember –membername “adventure-works\bobh” –database “AdventureWorks” –rolename “Reader”  
```  
  
 このコマンドは、既定のローカル インスタンス上で動作する AdventureWorks データベースの Reader ロールに Windows ドメイン ユーザー アカウントを追加します。  
  
## 例 2  
  
```  
PS SQLSERVER:\sqlas\localhost\default> $roles= dir .\databases\AWTEST\Roles  
PS SQLSERVER:\sqlas\localhost\default> $roles  
PS SQLSERVER:\sqlas\localhost\default> add-rolemember –membername:“adventure-works\bobh” –databaserole:$roles[0]  
```  
  
 行 1 は、AWTEST データベースのすべてのデータベース ロールをパイプラインに追加します。 行 2 のプロンプトで入力した「$roles」は、ロールの配列を示しています。 行 3 は、配列内の最初のロールのメンバーとして、Windows ユーザー "adventure-works\bobh" を追加します。  
  
## 例 3  
  
```  
PS SQLSERVER:\sqlas\localhost\default\Databases\AWTEST\Roles> $roles=dir  
PS SQLSERVER:\sqlas\localhost\default\Databases\AWTEST\Roles> $roles[0] | Add-rolemember –membername “adventure-works\bobh”  
```  
  
 このコマンドは、Windows ドメイン ユーザー アカウントを配列内の最初のロールに追加します。この配列は、特定のデータベース (AWTEST) のコンテキストで Roles フォルダーの子の一覧を表示することによって作成されたものです。  
  
## 参照  
 [PowerShell scripting in Analysis Services](../../analysis-services/instances/powershell-scripting-in-analysis-services.md)   
 [PowerShell を使用したテーブル モデルの管理](http://go.microsoft.com/fwlink/?linkID=227685)  
  
  