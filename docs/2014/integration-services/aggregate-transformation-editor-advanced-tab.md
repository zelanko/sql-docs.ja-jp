---
title: '[集計変換エディター] ([詳細設定] タブ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.aggregationtransformation.advanced.f1
helpviewer_keywords:
- Aggregate Transformation Editor
ms.assetid: 186a9736-2554-40a0-9cb2-877a8db5fde8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c437e15cbbcb3df64770ad0da4272eedf41cf0e9
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85439489"
---
# <a name="aggregate-transformation-editor-advanced-tab"></a>[集計変換エディター] ([詳細設定] タブ)
  **[集計変換エディター]** ダイアログ ボックスの **[詳細設定]** タブを使用すると、コンポーネントのプロパティの設定、集計の指定、入力列と出力列のプロパティの設定を行うことができます。  
  
> [!NOTE]  
>  キーの数、キー スケール、個別のキーの数、個別のキー スケールのオプションは、 **[詳細設定]** タブで指定した場合はコンポーネント レベル、 **[集計]** タブの [詳細設定] 画面で指定した場合は出力レベル、 **[集計]** タブの下部にある列の一覧で指定した場合は列レベルで適用されます。  
>   
>  集計変換では、 **[キー]** および **[キー スケール]** は、 **グループ化** 操作の結果として予想されるグループの数を示します。 **[個別カウント キー数]** および **[個別カウント スケール]** は、 **個別のカウント** 操作の結果として予想される個別の値の数を示します。  
  
 集計変換の詳細については、「 [集計変換](data-flow/transformations/aggregate-transformation.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **[キー スケール]**  
 集計で予想される、概算のキー数をオプションで指定します。 変換ではこの情報を使用して最初のキャッシュ サイズを最適化します。 既定では、このオプションの値は **[未指定]** です。 **[キー スケール]** と **[キーの数]** の両方が指定されている場合、 **[キーの数]** の方が優先されます。  
  
|[値]|説明|  
|-----------|-----------------|  
|指定されていません。|**[キー スケール]** プロパティは使用されません。|  
|Low|集計では約 500,000 キーを書き込むことができます。|  
|Medium|集計では約 5,000,000 キーを書き込むことができます。|  
|High|集計では 25,000,000 を超えるキーを書き込むことができます。|  
  
 **[キーの数]**  
 集計で予想される、正確なキー数をオプションで指定します。 変換ではこの情報を使用して最初のキャッシュ サイズを最適化します。 **[キー スケール]** と **[キーの数]** の両方が指定されている場合、 **[キーの数]** の方が優先されます。  
  
 **[個別カウント スケール]**  
 集計で書き込むことのできる個別の値の概数をオプションで指定します。 既定では、このオプションの値は **[未指定]** です。 **[個別カウント スケール]** と **[個別カウント キー数]** の両方が指定されている場合、 **[個別カウント キー数]** の方が優先されます。  
  
|[値]|説明|  
|-----------|-----------------|  
|指定されていません。|CountDistinctScale プロパティは使用されません。|  
|Low|集計では約 500,000 の個別の値を書き込むことができます。|  
|Medium|集計では約 5,000,000 の個別の値を書き込むことができます。|  
|High|集計では 25,000,000 を超える個別の値を書き込むことができます。|  
  
 **[個別カウント キー数]**  
 集計によって書き込むことのできる個別の値の正確な数をオプションで指定します。 **[個別カウント スケール]** と **[個別カウント キー数]** の両方が指定されている場合、 **[個別カウント キー数]** の方が優先されます。  
  
 **[自動拡張率]**  
 集計の際にメモリを拡張できる割合を 1 ～ 100% の範囲で指定します。 既定では、このオプションの値は **25%** です。  
  
## <a name="see-also"></a>関連項目  
 [Integration Services のエラーとメッセージの参照](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [集計変換エディター &#40;集計] タブ&#41;](../../2014/integration-services/aggregate-transformation-editor-aggregations-tab.md)   
 [集計変換を使用してデータセットの値を集計する](data-flow/transformations/aggregate-values-in-a-dataset-by-using-the-aggregate-transformation.md)  
  
  
