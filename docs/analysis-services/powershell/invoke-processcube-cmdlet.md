---
title: "Invoke-processcube コマンドレット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: b10ba7c1-8f10-4e72-9626-f9285e4341fd
caps.latest.revision: "9"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 5564256b3953c9173f433201506204d7ca24677e
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="invoke-processcube-cmdlet"></a>Invoke-ProcessCube コマンドレット
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]特定の処理の種類の変数を使用してキューブを処理します。  
  
>[!NOTE] 
>この記事には、古くなった情報と例があります。 最新バージョンには、Get-help コマンドレットを使用します。
  
## <a name="syntax"></a>構文  
 `Invoke-ProcessCube [-Name] <System.String> [-Database] <System.String> [-ProcessType] <Microsoft.AnalysisServices.ProcessType> [<CommonParameters>]`  
  
 `Invoke-ProcessCube –DatabaseCube <Microsoft.AnalysisServices.Cube> [-ProcessType] <Microsoft.AnalysisServices.ProcessType> [<CommonParameters>]`  
  
## <a name="description"></a>Description  
 Invoke-ProcessCube コマンドレットは、指定したレベルにキューブを処理します。 たとえば、ProcessFull は既存のデータをすべて新しいデータで上書きします。 キューブを処理する際は、処理の種類を指定する必要があります。 詳細については、「[処理オプションと設定 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-options-and-settings-analysis-services.md)」を参照してください。  
  
## <a name="parameters"></a>パラメーター  
  
### <a name="-name-string"></a>-名前\<文字列 >  
 処理するキューブを指定します。  
  
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
|位置|@shouldalert|  
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
  
### <a name="-databasecube-microsoftanalysissevicescube"></a>-Databasecube & \<Microsoft.AnalysisSevices.Cube >  
 処理する Microsoft.AnalysisServices.Cube オブジェクトを指定します。 パイプラインを介してキューブ名を渡す場合は、このパラメーターを使用します。  
  
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
|入力|なし|  
|出力|なし|  
  
## <a name="example-1"></a>例 1  
 `PS SQL SERVER:\sqlas\locahost\default\Databases\AWTEST\Cubes\Adventure Works > Get-Item .| Invoke-ProcessCube–ProcessType:ProcessDefault`  
  
 このコマンドは、処理対象のキューブの ID をパイプで渡しています。  
  
## <a name="example-2"></a>例 2  
 `PS SQL SERVER:\sqlas\locahost\default > Invoke-ProcessCube “Adventure Works” –database AWTEST –ProcessType:ProcessDefault`  
  
 このコマンドは、AWTEST データベースの Adventure Works キューブを処理します。   
  
  
