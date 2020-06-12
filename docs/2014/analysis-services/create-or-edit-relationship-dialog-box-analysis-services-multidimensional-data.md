---
title: '[リレーションシップの作成] または [リレーションシップの編集] ダイアログボックス (Analysis Services 多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dsvdesigner.createrelationship.f1
helpviewer_keywords:
- Create Relationship dialog box
ms.assetid: da3c7074-623e-4ddf-a707-d3276a47cf1c
author: minewiskan
ms.author: owend
ms.openlocfilehash: b18a0b6c79a3787af4a55a473e5203daf9c7308f
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84526485"
---
# <a name="create-or-edit-relationship-dialog-box-analysis-services---multidimensional-data"></a>[リレーションシップの作成] または [リレーションシップの編集] ダイアログ ボックス (Analysis Services - 多次元データ)
  **の** [リレーションシップの作成]/[リレーションシップの編集] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ダイアログ ボックスを使用すると、データ ソース ビューでリレーションシップを定義または変更できます。 **[リレーションシップの作成]/[リレーションシップの編集]** ダイアログ ボックスを表示するには、次の手順に従います。  
  
-   **データ ソース ビュー デザイナー** の **[ツール バー]** ペインで **[新しいリレーションシップ]** をクリックします。  
  
-   **データ ソース ビュー デザイナー** の **[テーブル]** ペインまたは **[ダイアグラム]** ペインのどちらかで、テーブルを右クリックして **[新しいリレーションシップ]** をクリックします。  
  
-   **データ ソース ビュー デザイナー** の **[ダイアグラム]** ペインでリレーションシップを右クリックして **[リレーションシップの編集]** をクリックします。  
  
> [!NOTE]  
>  **データソースビューデザイナー**では、基になるデータソースに存在しないリレーションシップを作成できます。また、**データソースビューデザイナー**によって作成されたリレーションシップを、基になるデータソースの既存の外部キーリレーションシップから削除することもできます。  
  
## <a name="options"></a>オプション  
 **[作成元 (外部キー) テーブル]**  
 作成先テーブルの 1 つまたは複数の列への参照を含むテーブルまたは名前付きクエリを選択します。  
  
 **[作成先 (主キー) テーブル]**  
 作成元テーブルによって参照されている 1 つまたは複数の列を含むテーブルを選択します。 自己結合の場合、 **[作成元 (外部キー) テーブル]** での選択と同じテーブルを選択します。  
  
 **[基になる列]**  
 作成先テーブルの列を参照する列を選択します。  
  
 **[対象になる列]**  
 作成元テーブルの列によって参照されている列を選択します。  
  
 **後ろ向き**  
 リレーションシップの方向を反転させます。  
  
 **説明**  
 リレーションシップの説明をオプションで入力します。  
  
## <a name="see-also"></a>参照  
 [多次元データ &#40;Analysis Services のデザイナーとダイアログボックス&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [データ ソース ビュー デザイナー (Analysis Services - 多次元データ)](data-source-view-designer-analysis-services-multidimensional-data.md)  
  
  
