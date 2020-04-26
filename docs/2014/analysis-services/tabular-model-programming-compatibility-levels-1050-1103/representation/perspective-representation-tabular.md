---
title: パースペクティブ表現 (表形式) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 6d2636c4-dae4-448f-a1d4-dbee739e177c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c4704fc56ae1eacfb8481533c9d743afff80e923
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/25/2020
ms.locfileid: "62757750"
---
# <a name="perspective-representation-tabular"></a>パースペクティブ表現 (テーブル)
  パースペクティブは、クライアント アプリケーション向けに、テーブル モデルをより小さな部分に簡素化したり絞りこんだりするメカニズムです。  
  
 パースペクティブ表現の作成および操作方法の詳細については、「[パースペクティブ表現 (表形式)](perspective-representation-tabular.md) 」を参照してください。  
  
> [!WARNING]  
>  パースペクティブはセキュリティ メカニズムではありません。パースペクティブの外にあるオブジェクトも、ユーザーは他のインターフェイスを利用してアクセスできます。  
  
## <a name="perspective-representation"></a>パースペクティブ表現  
 AMO オブジェクトの場合、パースペクティブ表現は <xref:Microsoft.AnalysisServices.Perspective> と一対一マッピングのリレーションシップにあり、その他の主要 AMO オブジェクトを必要としません。  
  
### <a name="perspective-in-amo"></a>AMO におけるパースペクティブ  
 次のコード スニペットでは、テーブル モデルでパースペクティブを作成する方法を示します。 このコードで中心となる要素は、perspectiveElements です。このオブジェクトは、ユーザーに提示されるテーブル モデルのすべてのオブジェクトをグラフィカルに表現したものです。 *perspectiveElements*には4つの列が含まれています。このシナリオでは、列1、2、および3のみが関連しています。 列 1 には表示される要素の型が格納されます (elementTypeValue)。列 2 には要素の完全な名前が格納されます。ほとんどの場合、この名前はパースペクティブに要素を入力するために解析する必要があります。列 3 にはチェック ボックスの項目が格納されます (checkedElement)。これによって、要素がパースペクティブに含まれているかどうかが指定されます。  
  
```  
  
private void updatePerspective_Click(  
                     AMO.Cube modelCube  
                  ,  DataGridView perspectiveElements  
                  ,  string updatedPerspectiveID  
             )  
{  
    //Update is done by delete first, create new and insert after  
    //if perspective doesn't exist then create first and insert after  
    updatedPerspectiveID = updatedPerspectiveID.Trim();  
    if (modelCube.Perspectives.Contains(updatedPerspectiveID))  
    {  
        modelCube.Perspectives.Remove(updatedPerspectiveID, true);  
        newDatabase.Update(AMO.UpdateOptions.ExpandFull, AMO.UpdateMode.UpdateOrCreate);  
    }  
    AMO.Perspective currentPerspective = modelCube.Perspectives.Add(updatedPerspectiveID, updatedPerspectiveID);  
  
    foreach (DataGridViewRow currentDGVRow in perspectiveElements.Rows)  
    {  
        bool checkedElement = (bool)currentDGVRow.Cells[3].Value;  
        if (checkedElement)  
        {  
            string elementTypeValue = currentDGVRow.Cells[1].Value.ToString();  
            string elementNameValue = currentDGVRow.Cells[2].Value.ToString();  
            switch (elementTypeValue)  
            {  
                case "Column: Attribute":  
                case "Column: Calculated Column":  
                    {  
                        string perspectiveDimensionName = Regex.Match(elementNameValue, @"(?<=')(.*?)(?=')").ToString();  
                        string perspectiveDimensionAttributeName = Regex.Match(elementNameValue, @"(?<=\[)(.*?)(?=\])").ToString();  
                        AMO.PerspectiveDimension currentPerspectiveDimension;  
                        if (!currentPerspective.Dimensions.Contains(perspectiveDimensionName))  
                        {  
                            currentPerspectiveDimension = currentPerspective.Dimensions.Add(perspectiveDimensionName);  
                        }  
                        else  
                        {  
                            currentPerspectiveDimension = currentPerspective.Dimensions[perspectiveDimensionName];  
                        }  
                        if (!currentPerspectiveDimension.Attributes.Contains(perspectiveDimensionAttributeName))  
                        {  
                            currentPerspectiveDimension.Attributes.Add(perspectiveDimensionAttributeName);  
                        }  
                    }  
                    break;  
                case "Hierarchy":  
                    {  
                        string perspectiveDimensionName = Regex.Match(elementNameValue, @"(?<=')(.*?)(?=')").ToString();  
                        string perspectiveDimensionHierarchyName = Regex.Match(elementNameValue, @"(?<=\[)(.*?)(?=\])").ToString();  
                        AMO.PerspectiveDimension currentPerspectiveDimension;  
                        if (!currentPerspective.Dimensions.Contains(perspectiveDimensionName))  
                        {  
                            currentPerspectiveDimension = currentPerspective.Dimensions.Add(perspectiveDimensionName);  
                        }  
                        else  
                        {  
                            currentPerspectiveDimension = currentPerspective.Dimensions[perspectiveDimensionName];  
                        }  
                        if (!currentPerspectiveDimension.Hierarchies.Contains(perspectiveDimensionHierarchyName))  
                        {  
                            currentPerspectiveDimension.Hierarchies.Add(perspectiveDimensionHierarchyName);  
                        }  
                    }  
                    break;  
                case "Measure":  
                    {  
                        string perspectiveMeasureGroupName = Regex.Match(elementNameValue, @"(?<=')(.*?)(?=')").ToString();  
                        string measureName = Regex.Match(elementNameValue, @"(?<=\[)(.*?)(?=\])").ToString();  
                        string perspectiveMeasureName = string.Format("[Measures].[{0}]", measureName);  
                        AMO.PerspectiveCalculation currentPerspectiveCalculation = new AMO.PerspectiveCalculation(perspectiveMeasureName, AMO.PerspectiveCalculationType.Member);  
                        if (!currentPerspective.Calculations.Contains(perspectiveMeasureName))  
                        {  
                            currentPerspective.Calculations.Add(currentPerspectiveCalculation);  
                        }  
                        if (modelCube.MdxScripts["MdxScript"].CalculationProperties.Contains(string.Format("KPIs.[{0}]", measureName)))  
                        {//Current Measure is also a KPI ==> will be added to the KPIs collection of the perspective  
                            AMO.PerspectiveKpi currentPerspectiveKpi = new AMO.PerspectiveKpi(perspectiveMeasureName);  
                            if (!currentPerspective.Kpis.Contains(perspectiveMeasureName))  
                            {  
                                currentPerspective.Kpis.Add(currentPerspectiveKpi);  
                            }  
                        }  
                    }  
                    break;  
                default:  
                    break;  
            }  
        }  
    }  
  
    newDatabase.Update(AMO.UpdateOptions.ExpandFull, AMO.UpdateMode.CreateOrReplace);  
    MessageBox.Show(String.Format("Perpective successfully updated."), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Information);  
}  
  
```  
  
## <a name="amo2tabular-sample"></a>AMO2Tabular サンプル  
 ただし、AMO を使用してパースペクティブ表現の作成と操作を行う方法については、AMO to Tabular サンプルのソース コードを参照してください。 このサンプルは、Codeplex から入手できます。 このコードに関する重要な注意事項: このコードは、ここで説明する論理的概念を補足するためにのみ提供されています。運用環境では使用しないでください。教育目的以外の目的にも使用しないでください。  
  
  
