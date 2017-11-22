---
title: "呼び出す ProcessASDatabase |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: powershell
ms.reviewer: 
ms.suite: sql
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 66d5d154-88ce-4c2e-b1ef-e2d2f6fb1c44
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 72c96cddc1d505906164aa3d634871ba0ae30072
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="invoke-processasdatabase"></a>Invoke-ProcessASDatabase

[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  基になるメタデータの種類に応じて、特定の **ProcessType** または **RefreshType** の指定した **Database** に対して **Process** 操作を実行します。  
  
 多次元メタデータを含むデータベースには、 **ProcessType** を使用します (互換性レベル 1050、1100、または 1103 の表形式のデータベースが含まれます)。  
  
 互換性レベル 1200 以降の表形式データベースには、 **RefreshType** を使用します。  

>[!NOTE] 
>この記事には、古くなった情報と例があります。 最新バージョンには、Get-help コマンドレットを使用します。
  
## <a name="syntax"></a>構文  
 `Invoke-ProcessASDatabase [-DatabaseName] <string> [-RefreshType] <RefreshType> {Full | ClearValues | Calculate |     DataOnly | Automatic | Add | Defragment} [-Server <string>] [-Credential <pscredential>] [-WhatIf] [-Confirm]     [<CommonParameters>]`  
  
 `Invoke-ProcessASDatabase [-DatabaseName] <string> [-ProcessType] <ProcessType> {ProcessFull | ProcessAdd |     ProcessUpdate | ProcessIndexes | ProcessData | ProcessDefault | ProcessClear | ProcessStructure |     ProcessClearStructureOnly | ProcessScriptCache | ProcessRecalc | ProcessDefrag} [-Server <string>] [-Credential     <pscredential>] [-WhatIf] [-Confirm]  [<CommonParameters>]`  
  
## <a name="description"></a>Description  
 **Invoke-ProcessASDatabase** コマンドレットは、指定したレベルまでデータベースを処理します。 たとえば、互換性レベル 1200 の表形式データベースの場合、既存のデータをすべて新しいデータで上書きするように **RefreshType** を **Full** に設定します。  
  
 処理の種類 (多次元) または更新の種類 (表形式) は必須です。データベースおよびサーバーのパラメーターの前後で指定できます。  
  
-   多次元については、「[処理オプションと設定 (Analysis Services)](../../analysis-services/multidimensional-models/processing-options-and-settings-analysis-services.md)」を参照してください。  
  
-   表形式については、「[データベース、テーブル、またはパーティションの処理 (Analysis Services)](../../analysis-services/tabular-models/process-database-table-or-partition-analysis-services.md)」を参照してください。  
  
## <a name="parameters"></a>パラメーター  
  
### <a name="-databasename-string"></a>-DatabaseName\<文字列 >  
 処理対象の表形式または多次元データベースを指定します。  
  
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
  
### <a name="-processtype-microsoftanalysisservicesprocesstype"></a>-Processtype & \<Microsoft.AnalysisServices.ProcessType >  
 互換性レベル 1050 ～ 1103 の多次元データベースまたは表形式データベースの場合、処理の種類を指定します。 有効な値は、ProcessFull、ProcessAdd、ProcessUpdate、ProcessIndexes、ProcessData、ProcessDefault、ProcessClear、ProcessStructure、ProcessCelarStructureOnly、ProcessScriptCache、または ProcessRecalc です。 説明とガイダンスについては、「[処理オプションと設定 (Analysis Services)](../../analysis-services/multidimensional-models/processing-options-and-settings-analysis-services.md)」を参照してください。  
  
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
  
## <a name="-whatif"></a>-Whatif  
 実行前に操作の影響に関する情報を取得するには、このパラメーターを含めます。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
## <a name="-confirm"></a>-Confirm  
 先に進む前に、[はい] または [いいえ] の応答で操作を確定する場合に、このパラメーターを含めます。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置||  
|既定値||  
|パイプライン入力の受け入れ||  
|ワイルドカード文字の受け入れ|オプション|  
  
## <a name="example-1-sqlas-provider"></a>例 1 (SQLAS プロバイダー)  
 この例では、 **SQLAS** プロバイダーを使用して、既定のインスタンスのデータベース一覧に対してコンテキストを設定します。  databases ディレクトリの内容を一覧表示すると、すべてのデータベースと、そのプロセスの状態および読み取り/書き込みモードを参照することができます。  
  
 databases フォルダーから、データベース名のみを指定して **Invoke-ProcessASDatabase** を実行できます。  
  
```  
PS > import-module SQLPS -DisableNameChecking  
PS  SQL Server > cd sqlas\ssas-srv-01\default\databases  
PS SQLSERVER:\sqlas\ssas-srv-01\default\databases> dir  
. . . .  
PS SQLSERVER:\sqlas\ssas-srv-01\default\databases> Invoke-ProcessASDatabase "adventureworks"  
  
```  
  
 データベースの種類に応じて、 **RefreshType** または **ProcessType**を指定するように求められます。  
  
 処理の証拠として、返信ステートメント Microsoft.AnalysisServices.Tabular.ObjectImpact に impact オブジェクトが存在します。  
  
 オブジェクトの状態情報はキャッシュされるため、処理の完了後、ディレクトリの内容を一覧表示すると、データベースの状態は元の ’unprocessed’ 記述子のままです。 objectimact が返された場合、実際にはデータベースは処理されているので、これは誤解を招きやすい状態です。  
  
 処理の成功を確認するには、Management Studio でデータベースのプロパティ ページを確認するか、新しいセッションを開始するか、または ( [Microsoft.AnalysisServices.ProcessableMajorObject.LastProcessed](https://msdn.microsoft.com/library/microsoft.analysisservices.processablemajorobject.lastprocessed.aspx)を使用して) データベース オブジェクトから処理状態を返します。  
  
## <a name="example-2"></a>例 2  
 この例では、プロバイダーを指定せずに、コマンドレットのみを使用して同じ操作を実行します。 サーバーとプロセスの種類を指定するには、追加のパラメーターが必要です。  
  
```  
PS > import-module SQLPS -DisableNameChecking  
PS  SQL Server >  Invoke-ProcessASDatabase -databasename "AdventureWorks" -server '\\server-name\instancename' –ProcessType "ProcessFull"  
  
```  
  
  
  
