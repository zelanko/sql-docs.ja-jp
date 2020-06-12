---
title: '[データソースビュー] ([ディメンション構造] タブ、ディメンションデザイナー) (Analysis Services 多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql.asvs.dimensiondesigner.dbv.datasourcepane.f1
ms.assetid: c4bd3c5e-8986-448f-b9db-3551f50f0696
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7136c984315714ba6726633522c8702b4c3a84f8
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84528918"
---
# <a name="data-source-view-dimension-structure-tab-dimension-designer-analysis-services---multidimensional-data"></a>[データ ソース ビュー] ([ディメンション構造] タブ、ディメンション デザイナー) (Analysis Services - 多次元データ)
  **[データ ソース ビュー]** ペインを使用すると、選択したディメンションに関連付けられているデータ ソース ビューからテーブルと列を表示できます。 **[データ ソース ビュー]** ペインでは、このペインから **[属性]** ペインまたは **[階層とレベル]** ペインに列をドラッグすることにより、属性、メンバー プロパティ、階層、およびレベルを作成します。  
  
## <a name="options"></a>オプション  
 **データソースビュー**  
 選択したディメンションに関連付けられたデータ ソース ビューを表示します。  
  
 **(表示領域の移動)**  
 ペインの右下隅のスクロール バーの間をクリックすると、表示する **[データ ソース ビュー]** ペインの領域を選択します。  
  
## <a name="diagram-context-menu"></a>ダイアグラムのショートカット メニュー  
 **[データ ソース ビュー]** ペインのダイアグラムの背景を右クリックすると表示されるショートカット メニューでは、次の表に示すオプションを使用できます。  
  
 **SHOW TABLES**  
 **[テーブルの表示]** ダイアログ ボックスを表示します。 **[テーブルの表示]** ダイアログ ボックスの詳細については、「[[テーブルの表示] ダイアログ ボックス (Analysis Services - 多次元データ)](show-table-dialog-box-analysis-services-multidimensional-data.md)」を参照してください。  
  
 **[すべてのテーブルを表示]**  
 ディメンションに関連付けられたデータ ソース ビューに含まれるすべてのテーブルをペインに表示します。  
  
 **[使用されたテーブルのみを表示]**  
 関連するデータ ソース ビューのディメンションによって使用されるテーブルのみをペインに表示します。  
  
 **フレンドリ名の表示**  
 ペイン内のオブジェクトの表示名を表示します。  
  
 **[すべて選択]**  
 ペイン内のすべてのオブジェクトが選択されます。  
  
 **[テーブルの検索]**  
 **[テーブルの検索]** ダイアログ ボックスを表示します。 **[テーブルの検索]** ダイアログ ボックスの詳細については、「[[テーブルの検索] ダイアログ ボックス (Analysis Services - 多次元データ)](find-table-dialog-box-analysis-services-multidimensional-data.md)」を参照してください。  
  
 **[テーブルの整列]**  
 **[斜線レイアウトに切り替え]** または **[四角形レイアウトに切り替え]** を選択して指定したレイアウトに従って、ペイン内のオブジェクトを並べ替えます。  
  
 **[斜線レイアウトに切り替え]**  
 オブジェクトを斜線パターンで整列できます。  
  
> [!NOTE]  
>   このオプションは、 **[四角形レイアウトに切り替え]** が選択されている場合にのみ表示されます。  
  
 **[四角形レイアウトに切り替え]**  
 オブジェクトを四角形パターンで整列できます。  
  
> [!NOTE]  
>   このオプションは、 **[斜線レイアウトに切り替え]** が選択されている場合にのみ表示されます。  
  
 **[データ ソース ビューの編集]**  
 ディメンションに関連付けられたデータ ソース ビューの**データ ソース ビュー デザイナー**を表示します。 **データ ソース ビュー デザイナー**の詳細については、「[データ ソース ビュー デザイナー &#40;Analysis Services - 多次元データ&#41;](data-source-view-designer-analysis-services-multidimensional-data.md)」を参照してください。  
  
 **[データ ソース ビューを表示]**  
 **[データ ソース ビュー]** ペインの表示モードとして、次のオプションのいずれかのオプションを選択します。  
  
-   ダイアグラム  
  
     現在のディメンションに関連付けられたテーブルと列のダイアグラムを表示します。  
  
-   ツリー  
  
     現在のディメンションに関連付けられたテーブルと列を含むツリー ビューを表示します。  
  
 **[ダイアグラムのコピー元]**  
 ディメンションに関連付けられたデータ ソース ビューに含まれるダイアグラムのいずれかを選択して、 **[データ ソース ビュー]** ペインに表示します。  
  
 **[ズーム]**  
 利用可能なズーム オプションを選択します。  
  
 **プロパティ**  
 ディメンションに関連付けられているデータ ソース ビューについて、 **SQL Server データ ツール** に **[プロパティ]** ウィンドウを表示します。  
  
## <a name="table-context-menu"></a>テーブルのショートカット メニュー  
 **[データ ソース ビュー]** ペインのテーブルまたはビューの名前を右クリックすると表示されるショートカット メニューでは、次のオプションを使用できます。  
  
 **[関連テーブルの表示]**  
 データ ソース ビューで選択されたテーブルに関連するテーブルをペインに表示します。  
  
 **[テーブルの非表示]**  
 ペインからテーブルを削除します。  
  
 **データの探索**  
 選択されているテーブルの **[データの探索]** ダイアログ ボックスを表示します。  
  
 **[データ ソース ビューの編集]**  
 選択したテーブルを含むデータソースビューの**データソースビューデザイナー**を表示します。 **データ ソース ビュー デザイナー**の詳細については、「[データ ソース ビュー デザイナー &#40;Analysis Services - 多次元データ&#41;](data-source-view-designer-analysis-services-multidimensional-data.md)」を参照してください。  
  
 **プロパティ**  
 **SQL Server データ ツール** で選択されているテーブルの **[プロパティ]** ウィンドウを表示します。  
  
## <a name="column-context-menu"></a>列のショートカット メニュー  
 **[データ ソース ビュー]** ペインのテーブルまたはビュー内の列の名前を右クリックすると表示されるショートカット メニューでは、次のオプションを使用できます。  
  
 **[列から新しい属性を作成]**  
 データ ソース ビューで選択されたテーブルに関連するテーブルをペインに表示します。  
  
 **データの探索**  
 選択した列が含まれるテーブルの **[データの探索]** ダイアログ ボックスが表示されます。  
  
 **[データ ソース ビューの編集]**  
 選択した列を含むデータソースビューの**データソースビューデザイナー**を表示します。 **データ ソース ビュー デザイナー**の詳細については、「[データ ソース ビュー デザイナー &#40;Analysis Services - 多次元データ&#41;](data-source-view-designer-analysis-services-multidimensional-data.md)」を参照してください。  
  
 **プロパティ**  
 **SQL Server データ ツール** で選択されている列の **[プロパティ]** ウィンドウを表示します。  
  
## <a name="relationship-context-menu"></a>リレーションシップのショートカット メニュー  
 **[データ ソース ビュー]** ペインのリレーションシップを右クリックすると表示されるショートカット メニューでは、次の表に示すオプションを使用できます。  
  
 **[データ ソース ビューの編集]**  
 選択したリレーションシップを含むデータソースビューの**データソースビューデザイナー**を表示します。 **データ ソース ビュー デザイナー**の詳細については、「[データ ソース ビュー デザイナー &#40;Analysis Services - 多次元データ&#41;](data-source-view-designer-analysis-services-multidimensional-data.md)」を参照してください。  
  
 **プロパティ**  
 選択したリレーションシップの **[プロパティ]** ウィンドウを [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] に表示します。  
  
## <a name="see-also"></a>参照  
 [ディメンションデザイナー &#40;ディメンションデザイナーの&#41; &#40;Analysis Services-多次元データ&#41;](dimension-structure-dimension-designer-analysis-services-multidimensional-data.md)   
 [ツールバー &#40;[ディメンション構造] タブ、ディメンションデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](toolbar-dimension-structure-designer-analysis-services-multidimensional-data.md)   
 [属性 &#40;[ディメンション構造] タブ、ディメンションデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](attributes-dimension-designer-analysis-services-multidimensional-data.md)   
 [階層 &#40;ディメンションデザイナーの [ディメンション構造] タブ、ディメンションデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](hierarchies-dimension-designer-analysis-services-multidimensional-data.md)  
  
  
