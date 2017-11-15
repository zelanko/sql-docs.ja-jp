---
title: "移行を評価するための PowerShell コマンドレット | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 117250d3-9982-47fe-94fd-6f29f6159940
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 618784e57397aaff751a602ddabab4687e3f229e
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="powershell-cmdlet-for-migration-evaluation"></a>移行を評価するための PowerShell コマンドレット
  Save-SqlMigrationReport コマンドレットは、SQL Server データベース内にある複数のオブジェクトの移行適合性を評価するツールです。 現時点では、このツールの使用はインメモリ OLTP の移行適合性の評価に制限されています。 このコマンドレットは、管理者特権の Windows PowerShell 環境と sqlps の両方で実行できます。  
  
## <a name="syntax"></a>構文  
  
```powershell  
Save-SqlMigrationReport [ -MigrationType OLTP ] [ -Server server -Database database [ -Object object_name ] ]  |  [ -InputObject smo_object ] -FolderPath path  
```  
  
#### <a name="parameters"></a>パラメーター  
 次の表では各パラメーターについて説明します。  
  
|パラメーター|説明|  
|----------------|-----------------|  
|MigrationType|コマンドレットが対象としている移行シナリオの種類。 現在、この値は既定値である OLTP のみになります。 省略可。|  
|[サーバー]|対象の SQL Server インスタンスの名前。 -InputObject パラメーターが指定されていない場合、Windows Powershell 環境では必須です。 SQLPS では省略可能です。|  
|データベース|対象の SQL Server データベースの名前。 -InputObject パラメーターが指定されていない場合、Windows Powershell 環境では必須です。 SQLPS では省略可能です。|  
|オブジェクト|対象のデータベース オブジェクトの名前。 テーブルまたはストアド プロシージャを指定できます。|  
|InputObject|コマンドレットが対象とする SMO オブジェクト。 -Server と -Database が指定されていない場合、Windows Powershell 環境では必須です。 SQLPS では省略可能です。|  
|FolderPath|コマンドレットによって生成されたレポートが格納されるフォルダー。 必須。|  
  
## <a name="results"></a>[結果]  
 -FolderPath パラメーターで指定したフォルダーには、Tables と Stored Procedures という名前の 2 つのフォルダーが作成されます。 対象のオブジェクトがテーブルの場合、レポートは Tables フォルダー内に生成されます。 ストアド プロシージャの場合は、レポートは Stored Procedures フォルダー内に生成されます。  
  
  
