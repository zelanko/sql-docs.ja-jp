---
title: "Invoke-processpartition コマンドレット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 516fab44-734e-425b-9bd0-b4aee1fd338f
caps.latest.revision: "9"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: dc03c77ffd4fc5ad02d234fa5c1bdc456234779b
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="invoke-processpartition-cmdlet"></a>Invoke-ProcessPartition コマンドレット
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]特定の処理の種類の変数を使用してパーティションを処理します。  

>[!NOTE] 
>この記事には、古くなった情報と例があります。 最新バージョンには、Get-help コマンドレットを使用します。
  
## <a name="syntax"></a>構文  
 `Invoke-ProcessPartition [-Name] <System.String> [-Database] <System.String> [-ProcessType] <Microsoft.AnalysisServices.ProcessType> [-CubeName] <System.String> [-MeasureGroupName] <System.String> [<CommonParameters>]`  
  
 `Invoke-ProcessPartition –DatabasePartition <Microsoft.AnalysisServices.Partition> [-ProcessType] <Microsoft.AnalysisServices.ProcessType> [<CommonParameters>]`  
  
## <a name="description"></a>Description  
 Invoke-ProcessParition コマンドレットは、指定したキューブおよびメジャー グループのために、Analysis Services データベースの特定のパーティションを処理します。 ProcessType 値により、操作のスコープが決定されます。 パーティションを処理する際は、処理の種類を指定する必要があります。 詳細については、「[Processing Options and Settings (Analysis Services)](../../analysis-services/multidimensional-models/processing-options-and-settings-analysis-services.md)」(処理オプションと設定 (Analysis Services)) を参照してください。  
  
## <a name="parameters"></a>パラメーター  
  
### <a name="-name-string"></a>-名前\<文字列 >  
 処理するパーティションを指定します。  
  
|||  
|-|-|  
|必須/省略可能|true|  
|位置|0|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-database-string"></a>-データベース\<文字列 >  
 キューブが属するデータベースを指定します。  
  
|||  
|-|-|  
|必須/省略可能|true|  
|位置|1|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-cubename-string"></a>-Cubename &\<文字列 >  
 メジャー グループが属するキューブを指定します。  
  
|||  
|-|-|  
|必須/省略可能|true|  
|位置|2|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-measuregroupname-string"></a>-Measuregroupname &\<文字列 >  
 パーティションが属するメジャー グループを指定します。  
  
|||  
|-|-|  
|必須/省略可能|true|  
|位置|2|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-databasepartition-microsoftanalysisservicespartition"></a>-Databasepartition & \<Microsoft.AnalysisServices.Partition >  
 処理するパーティションを指定します。  
  
|||  
|-|-|  
|必須/省略可能|true|  
|位置|2|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-processtype-microsoftanalysisservicesprocesstype"></a>-Processtype & \<Microsoft.AnalysisServices.ProcessType >  
 処理の種類を指定します: ProcessFull、ProcessAdd、ProcessUpdate、ProcessIndexes、ProcessData、ProcessDefault、ProcessClear、ProcessStructure、ProcessCelarStructureOnly、ProcessScriptCache、ProcessRecalc。  
  
|||  
|-|-|  
|必須/省略可能|true|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="commonparameters"></a>\<CommonParameters >  
 このコマンドレットは、-Verbose、-Debug、-ErrorAction、-ErrorVariable、-OutBuffer、および –OutVariable の共通パラメーターをサポートしています。 詳細については、「 [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825)」を参照してください。  
  
## <a name="inputs-and-outputs"></a>入力および出力  
 入力型は、コマンドレットにパイプできるオブジェクトの型です。 戻り値の型は、コマンドレットが返すオブジェクトの型です。  
  
|||  
|-|-|  
|入力|なし|  
|出力|なし|  
  
## <a name="example-1"></a>例 1  
 `PS SQL SERVER:\sqlas\locahost\default\Databases\AWTEST\Cubes\Adventure Works\MeasureGroups\Sales Orders\Partitions\Total_Orders_2004 > Get-Item .| Invoke-ProcessPartition –ProcessType:ProcessDefault`  
  
 このコマンドは、処理対象のパーティションの ID をパイプで渡しています。  
  
## <a name="example-2"></a>例 2  
 `PS SQL SERVER:\sqlas\locahost\default\Databases\AWTEST\Cubes\Adventure Works\MeasureGroups> Invoke-ProcessPartition –Name “Total_Orders_2003” –MeasureGroupname “Sales Order” –CubeName “Adventure Works” –database “AWTEST” –ProcessType “ProcessFull”`  
  
 このコマンドは、AWTEST データベースの Sales Orders メジャー グループ内の Total_Orders_2003 パーティションを処理します。  
  
  
  
