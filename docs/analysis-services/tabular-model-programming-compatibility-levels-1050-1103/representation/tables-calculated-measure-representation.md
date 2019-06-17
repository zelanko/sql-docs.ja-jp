---
title: 計算メジャー表現 (テーブル) |Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: eb14a3114edde51f55a0d540a9ab7c8aa7578de2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63019285"
---
# <a name="tables---calculated-measure-representation"></a>テーブル - 計算されるメジャー表現
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  計算されるメジャーとは、使用されるたびに評価される名前付き DAX 式です。  
  
## <a name="calculated-measure-representation"></a>計算されるメジャー表現  
  
### <a name="calculated-measure-in-amo"></a>AMO 内の計算されるメジャー  
 AMO を使用してテーブル モデルの計算されるメジャーを管理する場合、<xref:Microsoft.AnalysisServices.Command> オブジェクトの <xref:Microsoft.AnalysisServices.MdxScript> オブジェクトに定義されているメジャーと、論理的な計算されるメジャー オブジェクトが一対一で対応します。 各**計算されるメジャー**として定義されます、**メジャーの作成**内の式を<xref:Microsoft.AnalysisServices.Command>オブジェクトし、をセミコロンで区切られます。 すべてコレクションに対応して表形式モデルにメジャーが計算される**CREATE MEASURE**で 1 つのコマンド オブジェクト内で文字列を<xref:Microsoft.AnalysisServices.MdxScript>オブジェクト。 また、計算される各メジャーは、<xref:Microsoft.AnalysisServices.CalculationProperty> と一対一でマップされます。  
  
 次のコード スニペットは、計算されるメジャーの作成方法を示しています。  
  
```  
  
private void addCalculatedMeasure(  
                   AMO.Cube modelCube  
                 , string cmTableName  
                 , string cmName  
                 , string newCalculatedMeasureExpression  
             )  
{  
    //Verify input requirements  
    if (string.IsNullOrEmpty(cmName) || string.IsNullOrWhiteSpace(cmName))  
    {  
        MessageBox.Show(String.Format("Calculated Measure name is not defined."), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Error);  
        return;  
    }  
    if (string.IsNullOrEmpty(newCalculatedMeasureExpression) || string.IsNullOrWhiteSpace(newCalculatedMeasureExpression))  
    {  
        MessageBox.Show(String.Format("Calculated Measure expression is not defined."), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Error);  
        return;  
    }  
  
    StringBuilder measuresCommand = new StringBuilder();  
  
    AMO.MdxScript mdxScript = modelCube.MdxScripts["MdxScript"];  
  
    //ToDo: Verify if measure already exits and ask user what wants to do next  
  
    if (mdxScript.Commands.Count == 1)  
    {  
        measuresCommand.AppendLine("-------------------------------------------------------------");  
        measuresCommand.AppendLine("-- Tabular Model measures command (do not modify manually) --");  
        measuresCommand.AppendLine("-------------------------------------------------------------");  
        measuresCommand.AppendLine();  
        measuresCommand.AppendLine();  
        mdxScript.Commands.Add(new AMO.Command(measuresCommand.ToString()));  
  
    }  
    else  
    {  
        measuresCommand.Append(mdxScript.Commands[1].Text);  
    }  
    measuresCommand.AppendLine(string.Format("CREATE MEASURE '{0}'[{1}]={2};", cmTableName, cmName, newCalculatedMeasureExpression));  
  
    mdxScript.Commands[1].Text = measuresCommand.ToString();  
  
    if (!mdxScript.CalculationProperties.Contains(cmName))  
    {  
        AMO.CalculationProperty cp = new AMO.CalculationProperty(cmName, AMO.CalculationType.Member);  
        cp.FormatString = ""; // ToDo: Get formatting attributes for the member  
        cp.Visible = true;  
        mdxScript.CalculationProperties.Add(cp);  
    }  
  
    try  
    {  
        modelCube.Update(AMO.UpdateOptions.ExpandFull, AMO.UpdateMode.UpdateOrCreate);  
        MessageBox.Show(String.Format("Calculated Measure successfully defined."), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Information);  
    }  
    catch (AMO.OperationException amoOpXp)  
    {  
        MessageBox.Show(String.Format("Calculated Measure expression contains syntax errors, or references undefined or missspelled elements.\nError message: {0}", amoOpXp.Message), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Warning);  
        return;  
    }  
    catch (AMO.AmoException amoXp)  
    {  
        MessageBox.Show(String.Format("AMO exception accessing the server.\nError message: {0}", amoXp.Message), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Warning);  
        return;  
    }  
    catch (Exception)  
    {  
        throw;  
    }  
}  
  
```  
  
  
