---
title: 移行を評価するための PowerShell コマンドレット | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: in-memory-oltp
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 117250d3-9982-47fe-94fd-6f29f6159940
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 9c607ff40930af63838522eb6e4212aa5a079b6e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="powershell-cmdlet-for-migration-evaluation"></a>移行を評価するための PowerShell コマンドレット
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Save-SqlMigrationReport コマンドレットは、SQL Server データベース内にある複数のオブジェクトの移行適合性を評価するツールです。 現時点では、このツールの使用はインメモリ OLTP の移行適合性の評価に制限されています。 このコマンドレットは、管理者特権の Windows PowerShell 環境と sqlps の両方で実行できます。  
  
## <a name="syntax"></a>構文  
  
```powershell  
Save-SqlMigrationReport [ -MigrationType OLTP ] [ -Server server -Database database [ -Object object_name ] ]  |  [ -InputObject smo_object ] -FolderPath path  
```  
  
#### <a name="parameters"></a>パラメーター  
 次の表では各パラメーターについて説明します。  
  
|パラメーター|Description|  
|----------------|-----------------|  
|MigrationType|コマンドレットが対象としている移行シナリオの種類。 現在、この値は既定値である OLTP のみになります。 省略可。|  
|[サーバー]|対象の SQL Server インスタンスの名前。 -InputObject パラメーターが指定されていない場合、Windows Powershell 環境では必須です。 SQLPS では省略可能です。|  
|[データベース]|対象の SQL Server データベースの名前。 -InputObject パラメーターが指定されていない場合、Windows Powershell 環境では必須です。 SQLPS では省略可能です。|  
|Object|対象のデータベース オブジェクトの名前。 テーブルまたはストアド プロシージャを指定できます。|  
|InputObject|コマンドレットが対象とする SMO オブジェクト。 -Server と -Database が指定されていない場合、Windows Powershell 環境では必須です。 SQLPS では省略可能です。|  
|FolderPath|コマンドレットによって生成されたレポートが格納されるフォルダー。 必須。|  
  
## <a name="results"></a>[結果]  
 -FolderPath パラメーターで指定したフォルダーには、Tables と Stored Procedures という名前の 2 つのフォルダーが作成されます。 対象のオブジェクトがテーブルの場合、レポートは Tables フォルダー内に生成されます。 ストアド プロシージャの場合は、レポートは Stored Procedures フォルダー内に生成されます。  
  
  
