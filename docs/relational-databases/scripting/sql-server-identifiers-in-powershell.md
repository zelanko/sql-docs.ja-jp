---
title: "PowerShell での SQL Server 識別子 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "コマンドレット [SQL Server], Encode-Sqlname"
  - "PowerShell [SQL Server], 識別子"
  - "Encode-Sqlname コマンドレット"
  - "PowerShell [SQL Server], Encode-Sqlname"
  - "Decode-Sqlname コマンドレット"
  - "PowerShell [SQL Server], Decode-Sqlname"
  - "識別子 [SQL Server], PowerShell"
  - "コマンドレット [SQL Server], Decode-Sqlname"
ms.assetid: 651099b0-33b4-453a-a864-b067f21eb8b9
caps.latest.revision: 24
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 24
---
# PowerShell での SQL Server 識別子
  Windows PowerShell 用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロバイダーは、Windows Powershell のパスに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 識別子を使用します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 識別子には、Windows PowerShell でパスとしてサポートされない文字が含まれている場合があります。 Windows PowerShell パスでこの識別子を使用する場合は、これらの文字をエスケープするか、この文字に特殊なエンコードを使用する必要があります。  
  
## Windows PowerShell パス内の SQL Server 識別子  
 Windows PowerShell プロバイダーは、Windows ファイル システムで使用されるようなパス構造を使用してデータ階層を公開します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロバイダーは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトへのパスを実装します。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]については、ドライブが SQLSERVER: に、最初のフォルダーが \SQL に設定され、データベース オブジェクトがコンテナーおよびアイテムとして参照されます。 これは、[!INCLUDE[ssDE](../../includes/ssde-md.md)] の既定のインスタンスにある [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースの Purchasing スキーマ内の Vendor テーブルへのパスです。  
  
```  
SQLSERVER:\SQL\MyComputer\DEFAULT\Databases\AdventureWorks2012\Tables\Purchasing.Vendor  
```  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 識別子は、テーブル名や列名などの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトの名前です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 識別子には 2 つの種類があります。  
  
-   標準識別子には、Windows PowerShell パスでもサポートされている一連の文字のみを使用できます。 これらの名前は、変更することなく Windows PowerShell パスで使用できます。  
  
-   区切られた識別子には、Windows PowerShell パス名ではサポートされない文字を使用できます。 区切られた識別子には、角かっこで囲まれた識別子 ([IdentifierName]) と二重引用符で囲まれた識別子 ("IdentifierName") があります。 区切られた識別子に Windows PowerShell パスではサポートされない文字を使用する場合は、識別子をコンテナー名またはアイテム名として使用する前に、その文字をエンコードまたはエスケープする必要があります。 エンコードはすべての文字に有効です。 コロン (:) などの一部の文字は、エスケープできません。  
  
## コマンドレットでの SQL Server 識別子  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コマンドレットには、識別子を入力として使用するパラメーターを持つものがあります。 このパラメーターの値は、通常、引用符で囲まれた文字列定数として指定されるか、文字列変数で指定されます。 識別子を文字列定数または文字列変数で指定すると、Windows PowerShell でサポートされる一連の文字と競合することがありません。  
  
## SQL Server 識別子のタスク  
  
|タスクの説明|トピック|  
|----------------------|-----------|  
|インスタンス名 (インスタンスが実行されているコンピューターの名前を含む) の指定方法について説明します。|[SQL Server PowerShell プロバイダーでのインスタンスの指定](../../relational-databases/scripting/specify-instances-in-the-sql-server-powershell-provider.md)|  
|Windows PowerShell のパスでサポートされていない区切られた識別子において、文字の 16 進エンコードを指定する方法について説明します。 また、16 進文字をデコードする方法についても説明します。|[SQL Server 識別子のエンコードとデコード](../../relational-databases/scripting/encode-and-decode-sql-server-identifiers.md)|  
|Windows PowerShell のパスでサポートされない文字にエスケープ文字を使用する方法について説明します。|[SQL Server 識別子のエスケープ](../../relational-databases/scripting/escape-sql-server-identifiers.md)|  
  
## 参照  
 [SQL Server PowerShell プロバイダー](../../relational-databases/scripting/sql-server-powershell-provider.md)   
 [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md)   
 [データベース識別子](../../relational-databases/databases/database-identifiers.md)  
  
  