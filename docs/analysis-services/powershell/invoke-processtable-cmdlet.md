---
title: "Invoke-ProcessTable コマンドレット | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 865e6d06-b99a-41f3-9d6f-c3c97b529b23
caps.latest.revision: 9
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 9
---
# Invoke-ProcessTable コマンドレット
  特定の **RefreshType** を使用して、 **Table** に対して **Process**操作を実行します。  
  
 このコマンドレットは、SQL Server 2016 互換性レベル 1200 の表形式モデルにのみ適用されます。  
  
## 構文  
 `Invoke-ProcessTable [-DatabaseName] <string> [-TableName] <string> [-RefreshType] <RefreshType> {Full |     ClearValues | Calculate | DataOnly | Automatic | Add | Defragment} [-Server <string>] [-Credential <pscredential>     [-WhatIf] [-Confirm]  [<CommonParameters>]`  
  
 `Invoke-ProcessTable -RefreshType <RefreshType> {Full | ClearValues | Calculate | DataOnly | Automatic | Add |     Defragment} -Table <Table> [-Server <string>] [-Credential <pscredential>] [-WhatIf] [-Confirm]     [<CommonParameters>]`  
  
## パラメーター  
  
### -TableName \<string>  
 処理するパーティションが属するテーブルの名前。  
  
|||  
|-|-|  
|必須/省略可能|true|  
|位置|0|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### -DatabaseName \<string>  
 テーブルが属するデータベースを指定します。  
  
|||  
|-|-|  
|必須/省略可能|true|  
|位置|0|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### -Server\<Microsoft.AnalysisSevices.Server>  
 必要に応じて、コンテキストに **SQLAS** プロバイダー ディレクトリを使用しない場合に接続する先のサーバー インスタンスを指定します。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### -RefreshType \<Microsoft.AnalysisServices.RefreshType>  
 互換性レベル 1200 の表形式データベースのプロセスの種類を変更します。  有効な値は、Full、ClearValues、Calculate、DataOnly、Automatic、Add、および Defragment です。 説明とガイダンスについては、「[データベース、テーブル、またはパーティションの処理 &#40;Analysis Services&#41;](../../analysis-services/tabular-models/process-database-table-or-partition-analysis-services.md)」を参照してください。  
  
|||  
|-|-|  
|必須/省略可能|true|  
|位置|1|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### -Credential  
 このパラメーターを指定した場合は、Analysis Services インスタンスへの接続に、渡されたユーザー名とパスワードが使用されます。 資格情報を指定していない場合は、スクリプトを実行しているユーザーの既定の Windows アカウントが使用されます。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### -Whatif  
 実行前に操作の影響に関する情報を取得するには、このパラメーターを含めます。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### -Confirm  
 先に進む前に、[はい] または [いいえ] の応答で操作を確定する場合に、このパラメーターを含めます。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置||  
|既定値||  
|パイプライン入力の受け入れ||  
|ワイルドカード文字の受け入れ|オプション|  
  
## 例 1  
 `PS SQLSERVER:\SQLAS\MachineName\Instance\Databases\DB1\> Invoke-ProcessTable -TableName "myTable" -Database "DB1"  -RefreshType "Full"`  
  
 このコマンドは、処理対象のテーブルの ID をパイプで渡しています。  
  
## 例 2  
 `PS SQLSERVER:\SQLAS\MachineName\Instance\Databases\DB1\> Invoke-ProcessTable -TableName "myTable" -Database "DB1"  -RefreshType [Microsoft.AnalysisServices.Tabular.RefreshType]::Full`  
  
 このコマンドは、 **enum** 更新の種類を使用して、表形式メタデータ テーブルを処理します。  
  
## 参照  
 [Analysis Services での表形式モデルの互換性レベル](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)  
  
  