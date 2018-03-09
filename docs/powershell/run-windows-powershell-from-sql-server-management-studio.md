---
title: "SQL Server Management Studio から Windows PowerShell を実行する方法 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: powershell
ms.service: 
ms.component: powershell
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1f841825-da1f-4062-9a81-3cdbab03845b
caps.latest.revision: "11"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 762d038aba38b2cbcb8906b729179aca6a6f7835
ms.sourcegitcommit: 779f3398e4e3f4c626d81ae8cedad153bee69540
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2018
---
# <a name="run-windows-powershell-from-sql-server-management-studio"></a>SQL Server Management Studio から Windows PowerShell を実行する方法
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Windows PowerShell セッションは、 **の** オブジェクト エクスプローラー [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]から起動できます。 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] によって Windows PowerShell が起動され、**SqlServer** モジュールが読み込まれて、パス コンテキストが、**オブジェクト エクスプローラー** ツリー内の関連ノードに設定されます。  
  

> [!NOTE]
> SQL Server PowerShell モジュールには **SqlServer** と **SQLPS** の 2 つがあります。 **SQLPS** モジュールは (後方互換性のため) SQL Server のインストールに含まれていますが、今後更新されることはありません。 最新の PowerShell モジュールは **SqlServer** モジュールです。 **SqlServer** モジュールには **SQLPS** のコマンドレットの更新バージョンだけでなく、最新の SQL 機能をサポートする新しいコマンドレットも含まれています。  
> SQL Server Management Studio (SSMS) には前のバージョンの **SqlServer** が含まれて*いました*が、SSMS の 16.x バージョンのみです。 PowerShell を SSMS 17.0 以降で使用するには、**SqlServer** モジュールを PowerShell ギャラリーからインストールする必要があります。
> **SqlServer** モジュールをインストールする場合は、「[SQL Server PowerShell のインストール](download-sql-server-ps-module.md)」を参照してください。



**オブジェクト エクスプローラー**でオブジェクトに対して PowerShell の実行を指定すると、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] PowerShell スナップインの読み込みと登録が完了した Windows PowerShell セッションが [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] によって開始されます。 セッションのパスは、オブジェクト エクスプローラーで右クリックしたオブジェクトの場所にあらかじめ設定されています。 たとえば、オブジェクト エクスプローラーで [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] データベース オブジェクトを右クリックして **[PowerShell の起動]**を選択した場合、Windows PowerShell パスは次のように設定されます。  
  
```  
SQLSERVER:\SQL\MyComputer\MyInstance\Databases\AdventureWorks2012>  
```  
  
## <a name="run-powershell"></a>PowerShell の実行  
 **SQL Server Management Studio から PowerShell を実行するには**  
  
1.  **オブジェクト エクスプローラー**を開きます。  
  
2.  作業対象オブジェクトのノードに移動します。  
  
3.  オブジェクトを右クリックし、 **[PowerShell の起動]**を選択します。  
  
## <a name="permissions"></a>アクセス許可  
 PowerShell を [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] で開いた場合は管理者特権で実行されないため、WMI の呼び出しなどの一部のアクティビティが実行されない場合があります。  
  
## <a name="see-also"></a>参照  
 [SQL Server PowerShell](sql-server-powershell.md)  
  
  
