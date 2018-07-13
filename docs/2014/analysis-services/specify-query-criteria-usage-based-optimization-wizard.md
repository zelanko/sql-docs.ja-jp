---
title: クエリ条件 (使用法に基づく最適化ウィザード) の指定 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.usagebasedoptimizationwizard.specifyquerycriteria.f1
ms.assetid: 3193adc2-af9f-4234-a4cc-dea0c280a724
caps.latest.revision: 21
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 46a0877a1f51964287f9a01f00adeae23d2dcfd1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37176429"
---
# <a name="specify-query-criteria-usage-based-optimization-wizard"></a>[クエリ条件の指定] (使用法に基づく最適化ウィザード)
  **[クエリ条件の指定]** ページを使用すると、最適化するクエリを特定するために 1 つ以上のフィルター オプションを選択できます。  
  
> [!NOTE]  
>  このページは、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] がクエリ ログに接続できない場合は無効です。  
  
## <a name="options"></a>および  
 **クエリ ログの統計**  
 選択されたパーティションのクエリ ログに格納された、クエリに関する情報を表示します。 以下の項目が表示されます。  
  
|項目|定義|  
|----------|----------------|  
|**クエリの合計数**|選択されたパーティションのクエリ ログに格納された、クエリの合計数を表示します。|  
|**個別のクエリ**|選択されたパーティションのクエリ ログに格納された、異なるクエリの数を表示します。|  
|**個別のユーザー**|選択されたパーティションのクエリ ログに格納された、クエリに関連付けられた異なるユーザーの数を表示します。|  
|**平均応答時間**|選択されたパーティションのクエリ ログに格納された、クエリの平均応答時間を表示します。|  
  
 **開始日**  
 開始する日および時刻に基づいてクエリ ログのクエリをフィルターします。 日付をドロップダウン リストから選択するか入力します。  
  
> [!NOTE]  
>  **[終了日]** が選択されていない場合、このオプションで指定した日付および時刻以降のクエリ ログ内のすべてのクエリが対象になります。  
  
 **終了日**  
 終了する日および時刻に基づいてクエリ ログのクエリをフィルターします。 日付をドロップダウン リストから選択するか入力します。  
  
> [!NOTE]  
>  **[開始日]** が選択されていない場合、このオプションで指定した日付および時刻以前のクエリ ログ内のすべてのクエリが対象になります。  
  
 **ユーザー**  
 指定されたユーザーのセットに基づいてクエリ ログのクエリをフィルターします。 **[...]** ボタンをクリックして **[ユーザーの選択]** ダイアログ ボックスを開き、クエリをフィルターする対象ユーザーを選択します。 **[ユーザーの選択]** ダイアログ ボックスの詳細については、[「[ユーザーの選択] ダイアログ ボックス (Analysis Services - 多次元データ)」](user-selection-dialog-box-analysis-services-multidimensional-data.md) を参照してください。  
  
 **最も頻度の高いクエリ**  
 選択されたパーティションに対して、最も実行頻度の高いクエリの最大比率に基づいて、クエリ ログのクエリをフィルターします。 テキスト ボックスで比率の値を選択するか、値を入力します。  
  
## <a name="see-also"></a>参照  
 [使用法に基づく最適化ウィザードの F1 ヘルプ](usage-based-optimization-wizard-f1-help.md)   
 [Analysis Services のウィザード&#40;多次元データ&#41;](analysis-services-wizards-multidimensional-data.md)  
  
  
