---
title: "SQL Server Management Studio から Windows PowerShell を実行する方法 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1f841825-da1f-4062-9a81-3cdbab03845b
caps.latest.revision: 11
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 11
---
# SQL Server Management Studio から Windows PowerShell を実行する方法
  Windows PowerShell セッションは、 **の** オブジェクト エクスプローラー [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]から起動できます。 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]  によって Windows PowerShell が起動され、**sqlps** モジュールが読み込まれて、パス コンテキストが、**オブジェクト エクスプローラー** ツリー内の関連ノードに設定されます。  
  
## はじめに  
 **オブジェクト エクスプローラー**でオブジェクトに対して PowerShell の実行を指定すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell スナップインの読み込みと登録が完了した Windows PowerShell セッションが [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] によって開始されます。 セッションのパスは、オブジェクト エクスプローラーで右クリックしたオブジェクトの場所にあらかじめ設定されています。 たとえば、オブジェクト エクスプローラーで [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベース オブジェクトを右クリックして **[PowerShell の起動]** を選択した場合、Windows PowerShell パスは次のように設定されます。  
  
```  
SQLSERVER:\SQL\MyComputer\MyInstance\Databases\AdventureWorks2012>  
```  
  
## PowerShell の実行  
 **SQL Server Management Studio から PowerShell を実行するには**  
  
1.  **オブジェクト エクスプローラー**を開きます。  
  
2.  作業対象オブジェクトのノードに移動します。  
  
3.  オブジェクトを右クリックし、**[PowerShell の起動]** を選択します。  
  
## 権限  
 PowerShell を [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] で開いた場合は管理者特権で実行されないため、WMI の呼び出しなどの一部のアクティビティが実行されない場合があります。  
  
## 参照  
 [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md)  
  
  