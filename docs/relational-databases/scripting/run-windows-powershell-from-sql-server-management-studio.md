---
title: "SQL Server Management Studio から Windows PowerShell を実行する方法 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: ssms
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1f841825-da1f-4062-9a81-3cdbab03845b
caps.latest.revision: "11"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 2f3f405a8a0a64d1202918154a163bf9b397ab93
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="run-windows-powershell-from-sql-server-management-studio"></a>SQL Server Management Studio から Windows PowerShell を実行する方法
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Windows PowerShell セッションは、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の**オブジェクト エクスプローラー**から起動できます。 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] によって Windows PowerShell が起動され、 **sqlps** モジュールが読み込まれて、パス コンテキストが、 **オブジェクト エクスプローラー** ツリー内の関連ノードに設定されます。  
  
## <a name="before-you-begin"></a>はじめに  
 **オブジェクト エクスプローラー**でオブジェクトに対して PowerShell の実行を指定すると、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] PowerShell スナップインの読み込みと登録が完了した Windows PowerShell セッションが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって開始されます。 セッションのパスは、オブジェクト エクスプローラーで右クリックしたオブジェクトの場所にあらかじめ設定されています。 たとえば、オブジェクト エクスプローラーで [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベース オブジェクトを右クリックして **[PowerShell の起動]**を選択した場合、Windows PowerShell パスは次のように設定されます。  
  
```  
SQLSERVER:\SQL\MyComputer\MyInstance\Databases\AdventureWorks2012>  
```  
  
## <a name="run-powershell"></a>PowerShell の実行  
 **SQL Server Management Studio から PowerShell を実行するには**  
  
1.  **オブジェクト エクスプローラー**を開きます。  
  
2.  作業対象オブジェクトのノードに移動します。  
  
3.  オブジェクトを右クリックし、 **[PowerShell の起動]**を選択します。  
  
## <a name="permissions"></a>権限  
 PowerShell を [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]で開いた場合は管理者特権で実行されないため、WMI の呼び出しなどの一部のアクティビティが実行されない場合があります。  
  
## <a name="see-also"></a>参照  
 [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md)  
  
  
