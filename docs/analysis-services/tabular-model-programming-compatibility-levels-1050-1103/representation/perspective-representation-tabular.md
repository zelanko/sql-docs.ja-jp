---
title: パースペクティブ表現 (テーブル) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 6d2636c4-dae4-448f-a1d4-dbee739e177c
caps.latest.revision: 8
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: cd5dbe6ecadff60f3ab6c4bd0ef04f3b8500a5ee
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="perspective-representation-tabular"></a>パースペクティブ表現 (テーブル)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  パースペクティブは、クライアント アプリケーション向けに、テーブル モデルをより小さな部分に簡素化したり絞りこんだりするメカニズムです。  
  
 参照してください[パースペクティブ表現 (テーブル)](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/perspective-representation-tabular.md)を作成して、パースペクティブ表現を操作する方法の詳細についてはします。  
  
> [!WARNING]  
>  パースペクティブはセキュリティ メカニズムではありません。パースペクティブの外にあるオブジェクトも、ユーザーは他のインターフェイスを利用してアクセスできます。  
  
## <a name="perspective-representation"></a>パースペクティブ表現  
 AMO オブジェクトの場合、パースペクティブ表現は <xref:Microsoft.AnalysisServices.Perspective> と一対一マッピングのリレーションシップにあり、その他の主要 AMO オブジェクトを必要としません。  
  
### <a name="perspective-in-amo"></a>AMO におけるパースペクティブ  
 次のコード スニペットでは、テーブル モデルでパースペクティブを作成する方法を示します。 このコードで中心となる要素は、perspectiveElements です。このオブジェクトは、ユーザーに提示されるテーブル モデルのすべてのオブジェクトをグラフィカルに表現したものです。 *perspectiveElements* 4 つの列が含まれています。 このシナリオのみでは列 1、2 および 3 が関連するとします。 列 1 には表示される要素の型が格納されます (elementTypeValue)。列 2 には要素の完全な名前が格納されます。ほとんどの場合、この名前はパースペクティブに要素を入力するために解析する必要があります。列 3 にはチェック ボックスの項目が格納されます (checkedElement)。これによって、要素がパースペクティブに含まれているかどうかが指定されます。  
  
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
 ただし、理解を使用する方法の作成およびパースペクティブ表現を操作するのには AMO を参照してください、AMO to Tabular サンプルのソース コードです。 このサンプルは、Codeplex から入手できます。 このコードに関する重要な注意事項: このコードは、ここで説明する論理的概念を補足するためにのみ提供されています。運用環境では使用しないでください。教育目的以外の目的にも使用しないでください。  
  
  
