---
title: "Invoke-processdimension コマンドレット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 9506938e-7f9f-4595-ad6d-98c8b0ce8395
caps.latest.revision: "9"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: afe8c26b63babadc5a153dac60b15ec2c98e2033
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="invoke-processdimension-cmdlet"></a>Invoke-ProcessDimension コマンドレット
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]特定の処理の種類の変数を使用して、ディメンションを処理します。  

>[!NOTE] 
>この記事には、古くなった情報と例があります。 最新バージョンには、Get-help コマンドレットを使用します。
  
## <a name="syntax"></a>構文  
 `Invoke-ProcessDimension [-Name] <System.String> [-Database] <System.String> [-ProcessType] <Microsoft.AnalysisServices.ProcessType> [<CommonParameters>]`  
  
 `Invoke-ProcessDimension –DatabaseDimension <Microsoft.AnalysisServices.Dimension> [-ProcessType] <Microsoft.AnalysisServices.ProcessType> [<CommonParameters>]`  
  
## <a name="description"></a>Description  
 Invoke-ProcessDimension は、指定されたディメンションを処理するコマンドレットです。 処理の種類を指定する必要があります。 ディメンションの処理の種類の詳細については、「[処理オプションと設定 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-options-and-settings-analysis-services.md)」を参照してください。  
  
## <a name="parameters"></a>パラメーター  
  
### <a name="-name-string"></a>-名前\<文字列 >  
 処理するディメンションを指定します。  
  
|||  
|-|-|  
|必須/省略可能|true|  
|位置|0|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-database-string"></a>-データベース\<文字列 >  
 ディメンションが属するデータベースを指定します。  
  
|||  
|-|-|  
|必須/省略可能|true|  
|位置|1|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-processtype-microsoftanalysisservicesprocesstype"></a>-Processtype & \<Microsoft.AnalysisServices.ProcessType >  
 処理の種類を指定します: ProcessFull、ProcessAdd、ProcessUpdate、ProcessIndexes、ProcessData、ProcessDefault、ProcessClear、ProcessStructure、ProcessCelarStructureOnly、ProcessScriptCache、ProcessRecalc。  
  
|||  
|-|-|  
|必須/省略可能|true|  
|位置|2|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-databasedimension-microsoftanalysissevicesdimension"></a>-Databasedimension & \<Microsoft.AnalysisSevices.Dimension >  
 処理する Microsoft.AnalysisServices.Dimension オブジェクトを指定します。 パイプラインを介してディメンション名を渡す場合は、このパラメーターを使用します。  
  
|||  
|-|-|  
|必須/省略可能|true|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|可 (ByPropertyName)|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="commonparameters"></a>\<CommonParameters >  
 このコマンドレットは、-Verbose、-Debug、-ErrorAction、-ErrorVariable、-OutBuffer、および –OutVariable の共通パラメーターをサポートしています。 詳細については、「 [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825)」を参照してください。  
  
## <a name="inputs-and-outputs"></a>入力および出力  
 入力型は、コマンドレットにパイプできるオブジェクトの型です。 戻り値の型は、コマンドレットが返すオブジェクトの型です。  
  
|||  
|-|-|  
|入力|Microsoft.AnalysisSevices.Dimension|  
|出力|なし|  
  
## <a name="example-1"></a>例 1  
 `PS SQL SERVER:\sqlas\locahost\default\Databases\AWTEST\Dimensions\Account> Get-Item .| Invoke-ProcessDimension –ProcessType:ProcessDefault`  
  
 このコマンドは、指定されたディメンション オブジェクトをパイプラインを介して取得し、処理します。  
  
## <a name="example-2"></a>例 2  
 `PS SQL SERVER:\sqlas\locahost\default\Databases\AWTEST\Dimensions > Invoke-ProcessDimension –Name “Customer” –Database “AWTEST” –ProcessType “ProcessDefault”`  
  
 このコマンドは、処理の対象となる特定のディメンションを識別します。  
  
> [!NOTE]  
>  PowerShell ウィンドウでディメンション フォルダーを一覧表示したときに、正常に処理されたディメンションが "未処理" として表示される場合があります。 ディメンションが実際に処理されているかどうかを確認するには、SQL Server Management Studio でディメンションのプロパティをチェックしてください。  
  
  
  
