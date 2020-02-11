---
title: '[エラーの構成] ([マイニング構造] ダイアログボックス) (Analysis Services-多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.miningstructuredialog.general.f1
ms.assetid: d9aa028b-bad9-49c7-a81c-c2150e4dd481
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e8973d9dd6fb5d96afc9cf66ded4b894f0dfe6df
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66081371"
---
# <a name="error-configuration-mining-structure-dialog-box-analysis-services---multidimensional-data"></a>[エラーの構成] ([マイニング構造] ダイアログ ボックス) (Analysis Services - 多次元データ)
  
  **SQL Server Management Studio** で **[マイニング構造のプロパティ]** ダイアログ ボックスの **[エラーの構成]** ページを使用すると、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベース内のマイニング構造のエラー構成プロパティを設定できます。  
  
## <a name="options"></a>オプション  
 **既定のエラー構成を使用する**  
 処理操作でオブジェクトに対して既定のエラー構成を使用します。  
  
 **キーエラーアクション**  
 参照できない処理の間に新しいキーが検出されたとき、発生するアクションを次の中から 1 つ選択します。  
  
-   [**不明な種類に変換する**レコードの情報を不明なメンバーに集計します。  
  
-   **レコードの破棄**は、レコードの情報をオブジェクトで処理することを除外します。  
  
 **エラー数を無視する**  
 処理中に発生するエラーは、すべて無視します。  
  
 **エラー時に停止**  
 エラーが発生した場合、処理を停止します。 このオプションによって、 **[エラー数]** オプションおよび **[エラー時のアクション]** オプションが有効になります。  
  
 **エラーの数**  
 処理が停止される前に無視できるエラーの数を入力します。  
  
 **エラー時のアクション**  
 エラー数が **[エラー数]** の値を超えたときに行うアクションを次の中から 1 つ選択します。  
  
-   処理の**停止**は処理操作を終了します。  
  
-   **ログの停止**は、エラーのログ記録を停止しますが、処理操作は続行されます。  
  
 **キーが見つかりません**  
 オブジェクトの処理の際にキーが見つからなかった場合に行うアクションを次の中から 1 つ指定します。  
  
-   [**エラーを無視**する] エラーを無視します  
  
-   **レポートと続行**でエラーを報告し、処理操作を続行します  
  
-   **レポートと停止**は、エラーを報告し、処理操作を停止します。  
  
 **重複するキー**  
 オブジェクトの処理の際に重複キーが見つかった場合に行うアクションを次の中から 1 つ指定します。  
  
-   [**エラーを無視**する] エラーを無視します  
  
-   **レポートと続行**でエラーを報告し、処理操作を続行します  
  
-   **レポートと停止**は、エラーを報告し、処理操作を停止します。  
  
 **Null キーが不明な値に変換されました**  
 オブジェクトの処理の際に NULL メンバー キーが不明なメンバーに追加された場合に行うアクションを次の中から 1 つ指定します。  
  
-   [**エラーを無視**する] エラーを無視します  
  
-   **レポートと続行**でエラーを報告し、処理操作を続行します  
  
-   **レポートと停止**は、エラーを報告し、処理操作を停止します。  
  
 **Null キーは使用できません**  
 オブジェクトの処理の際に NULL キーが見つかったが許可されていない場合に行うアクションを次の中から 1 つ指定します。  
  
-   [**エラーを無視**する] エラーを無視します  
  
-   **レポートと続行**でエラーを報告し、処理操作を続行します  
  
-   **レポートと停止**は、エラーを報告し、処理操作を停止します。  
  
 **エラーログのパス**  
 エラー ログ ファイルの完全なパスとファイル名を入力します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services データマイニング&#41;&#40;マイニング構造のプロパティ] ダイアログボックス](mining-structure-properties-dialog-analysis-services-data-mining.md)   
 [[全般 &#40;[マイニング構造] ダイアログボックス&#41; &#40;Analysis Services-データマイニング&#41;](general-mining-structure-dialog-box-analysis-services-data-mining.md)  
  
  
