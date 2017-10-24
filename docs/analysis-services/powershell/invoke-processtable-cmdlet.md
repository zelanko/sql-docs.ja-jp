---
title: "Invoke-processtable コマンドレット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 865e6d06-b99a-41f3-9d6f-c3c97b529b23
caps.latest.revision: 9
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d2298c9e882f3f754b16ce33bf6bc72dfc6d80ff
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="invoke-processtable-cmdlet"></a>Invoke-ProcessTable コマンドレット

[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  特定の **RefreshType** を使用して、 **Table** に対して **Process**操作を実行します。  

>[!NOTE] 
>この記事には、古くなった情報と例があります。 最新バージョンには、Get-help コマンドレットを使用します。
  
## <a name="syntax"></a>構文  
 `Invoke-ProcessTable [-DatabaseName] <string> [-TableName] <string> [-RefreshType] <RefreshType> {Full |     ClearValues | Calculate | DataOnly | Automatic | Add | Defragment} [-Server <string>] [-Credential <pscredential>     [-WhatIf] [-Confirm]  [<CommonParameters>]`  
  
 `Invoke-ProcessTable -RefreshType <RefreshType> {Full | ClearValues | Calculate | DataOnly | Automatic | Add |     Defragment} -Table <Table> [-Server <string>] [-Credential <pscredential>] [-WhatIf] [-Confirm]     [<CommonParameters>]`  
  
## <a name="parameters"></a>パラメーター  
  
### <a name="-tablename-string"></a>-TableName\<文字列 >  
 処理するパーティションが属するテーブルの名前。  
  
|||  
|-|-|  
|必須/省略可能|true|  
|位置|0|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-databasename-string"></a>-DatabaseName\<文字列 >  
 テーブルが属するデータベースを指定します。  
  
|||  
|-|-|  
|必須/省略可能|true|  
|位置|0|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-servermicrosoftanalysissevicesserver"></a>-サーバー\<Microsoft.AnalysisSevices.Server >  
 必要に応じて、コンテキストに **SQLAS** プロバイダー ディレクトリを使用しない場合に接続する先のサーバー インスタンスを指定します。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-refreshtype-microsoftanalysisservicesrefreshtype"></a>-RefreshType \<Microsoft.AnalysisServices.RefreshType >  
 表形式データベースのプロセスの種類を指定します。  有効な値は、Full、ClearValues、Calculate、DataOnly、Automatic、Add、および Defragment です。 説明とガイダンスについては、「[データベース、テーブル、またはパーティションの処理 (Analysis Services)](../../analysis-services/tabular-models/process-database-table-or-partition-analysis-services.md)」を参照してください。  
  
|||  
|-|-|  
|必須/省略可能|true|  
|位置|1|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-credential"></a>-Credential  
 このパラメーターを指定した場合は、Analysis Services インスタンスへの接続に、渡されたユーザー名とパスワードが使用されます。 資格情報を指定していない場合は、スクリプトを実行しているユーザーの既定の Windows アカウントが使用されます。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-whatif"></a>-Whatif  
 実行前に操作の影響に関する情報を取得するには、このパラメーターを含めます。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-confirm"></a>-Confirm  
 先に進む前に、[はい] または [いいえ] の応答で操作を確定する場合に、このパラメーターを含めます。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置||  
|既定値||  
|パイプライン入力の受け入れ||  
|ワイルドカード文字の受け入れ|オプション|  
  
## <a name="example-1"></a>例 1  
 `PS SQLSERVER:\SQLAS\MachineName\Instance\Databases\DB1\> Invoke-ProcessTable -TableName "myTable" -Database "DB1"  -RefreshType "Full"`  
  
 このコマンドは、処理対象のテーブルの ID をパイプで渡しています。  
  
## <a name="example-2"></a>例 2  
 `PS SQLSERVER:\SQLAS\MachineName\Instance\Databases\DB1\> Invoke-ProcessTable -TableName "myTable" -Database "DB1"  -RefreshType [Microsoft.AnalysisServices.Tabular.RefreshType]::Full`  
  
 このコマンドは、 **enum** 更新の種類を使用して、表形式メタデータ テーブルを処理します。  
  
  

