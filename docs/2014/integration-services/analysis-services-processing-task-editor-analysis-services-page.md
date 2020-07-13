---
title: Analysis Services 処理タスクエディター (Analysis Services] ページ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.asprocessingtask.as.f1
helpviewer_keywords:
- Analysis Services Processing Task Editor
ms.assetid: 5612be78-57cf-4e4e-92cf-6bfa9f971040
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0ab462b751215ed6573de20764f3dee0715e5f33
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85439469"
---
# <a name="analysis-services-processing-task-editor-analysis-services-page"></a>[Analysis Services 処理タスク エディター] ([Analysis Services] ページ)
  **[Analysis Services 処理タスク エディター]** ダイアログ ボックスの **[Analysis Services]** ページを使用すると、Analysis Services 接続マネージャーの指定、処理する分析オブジェクトの選択、処理およびエラー処理オプションの設定を行うことができます。  
  
 テーブル モデルを処理する場合は、次の点に注意してください。  
  
1.  テーブル モデルでは影響分析を実行できません。  
  
2.  テーブル モード用のいくつかの処理オプションが表示されません ([デフラグの処理] や [再計算の処理] など)。 これらの機能は DDL 実行タスクを使用すると実行できます。  
  
3.  提供されているいくつかの処理オプション ([インデックスの処理] など) はテーブル モデルには適していないので、使用しないでください。  
  
4.  テーブル モデルでは、バッチ設定が無視されます。  
  
 このタスクの詳細については、「 [Analysis Services 処理タスク](control-flow/analysis-services-processing-task.md)」をご覧ください。  
  
## <a name="options"></a>オプション  
 **Analysis Services 接続マネージャー**  
 既存の Analysis Services 接続マネージャーを一覧から選択するか、 **[新規作成]** をクリックして新しい接続マネージャーを作成します。  
  
 **[新規作成]**  
 新しい Analysis Services 接続マネージャーを作成します。  
  
 **関連トピック:** [Analysis Services Connection Manager](connection-manager/analysis-services-connection-manager.md)、 [[Analysis Services 接続マネージャーの追加] ダイアログ ボックスの UI リファレンス](connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md)  
  
 **オブジェクトの一覧**  
 |プロパティ|説明|  
|--------------|-----------------|  
|**[オブジェクト名]**|指定されたオブジェクト名を表示します。|  
|**Type**|指定されたオブジェクトの種類を表示します。|  
|**[処理オプション]**|一覧から処理オプションを選択します。<br /><br /> **関連トピック**:[多次元モデルオブジェクトの処理](https://docs.microsoft.com/analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services)|  
|**設定**|指定されたオブジェクトの処理設定を表示します。|  
  
 **[追加]**  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] オブジェクトを一覧に追加します。  
  
 **[削除]**  
 オブジェクトを選択し、 **[削除]** をクリックします。  
  
 **[影響分析]**  
 選択したオブジェクトに対して影響分析を実行します。  
  
 **関連トピック:** [[影響分析] ダイアログ ボックス (Analysis Services - 多次元データ)](../../2014/analysis-services/impact-analysis-dialog-box-analysis-services-multidimensional-data.md)  
  
 **[バッチ設定の概要]**  
 |プロパティ|説明|  
|--------------|-----------------|  
|**処理順序**|オブジェクトを順番に処理するか、一括して処理するかを指定します。並行処理を行う場合は、同時に処理するオブジェクトの数を指定します。|  
|**[トランザクション モード]**|順次処理のトランザクション モードを指定します。|  
|**[ディメンション エラー]**|エラーが発生したときのタスクの動作を指定します。|  
|**[ディメンション キーのエラー ログのパス]**|エラーを記録するファイルのパスを指定します。|  
|**影響を受けるオブジェクトの処理**|依存オブジェクトまたは影響を受けたオブジェクトも処理するかどうかを示します。|  
  
 **設定の変更**  
 処理オプションおよびディメンション キー内のエラー処理を変更します。  
  
 **関連トピック:** [[設定の変更] ダイアログ ボックス (Analysis Services - 多次元データ)](../../2014/analysis-services/change-settings-dialog-box-analysis-services-multidimensional-data.md)  
  
## <a name="see-also"></a>関連項目  
 [Integration Services のエラーとメッセージの参照](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Analysis Services 処理タスクエディター &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md)   
 [Analysis Services DDL 実行タスク](control-flow/analysis-services-execute-ddl-task.md)  
  
  
