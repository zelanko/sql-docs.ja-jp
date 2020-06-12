---
title: '[計算ツール] (キューブデザイナーの [アクション] タブ) (Analysis Services 多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.actionsview.calculationtoolspane.f1
ms.assetid: a3370370-43cd-4cc2-bb9f-c0d988b96f05
author: minewiskan
ms.author: owend
ms.openlocfilehash: 42336656ce19d36cf0eadc986450dd8f3b81f669
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84527645"
---
# <a name="calculation-tools-actions-tab-cube-designer-analysis-services---multidimensional-data"></a>[計算ツール] (キューブ デザイナーの [アクション] タブ) (Analysis Services - 多次元データ)
  キューブ デザイナーの **[アクション]** タブの **[計算ツール]** ペインを使用すると、アクション、ドリルスルー アクション、およびレポート アクションで使用可能なメタデータ、関数、およびテンプレートを調査できます。  
  
## <a name="options"></a>オプション  
 **Metadata**  
 選択したキューブのメタデータを表示します。  
  
 選択した要素を **アクション フォーム エディター**ペイン、 **ドリルスルー アクション フォーム エディター**ペイン、または **レポート アクション フォーム エディター** ペインにドラッグし、ペイン内の選択した場所にその要素の多次元式 (MDX) 構文を含めます。  
  
 **関数**  
 式および条件で使用可能な関数を表示します。  
  
 選択した要素を **アクション フォーム エディター**ペイン、 **ドリルスルー アクション フォーム エディター**ペイン、または **レポート アクション フォーム エディター** ペインにドラッグし、ペイン内の選択した場所にその要素の MDX 構文を含めます。  
  
> [!NOTE]  
>  プロジェクト モードでは、 **[計算ツール]** ダイアログ ボックスは [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]に付属している MDXFunctions.xml という名前の XML ファイルから、このオプションについての情報を読み取ります。 オンライン モードでは、このオプションについての情報は、このインスタンスの MDSCHEMA_FUNCTIONS スキーマ行セットから取得します。  
  
 **テンプレート**  
 アクションで使用可能な定義済みテンプレートを表示します。  
  
 選択した要素を **アクション フォーム エディター**ペイン、 **ドリルスルー アクション フォーム エディター**ペイン、または **レポート アクション フォーム エディター** ペインにドラッグし、ペイン内の選択した場所にその要素の MDX 構文を含めます。  
  
## <a name="context-menu"></a>コンテキスト メニュー  
 **[計算ツール]** ペインで要素を右クリックして表示されるショートカット メニューでは、次のオプションを使用できます。  
  
|オプション|定義|  
|------------|----------------|  
|**コピー**|**[メタデータ]** または **[関数]** で選択した要素をクリップボードにコピーします。<br /><br /> **テンプレート**が選択されている場合、このオプションは表示されないことに注意してください。 また、**メタデータ**に表示されるディメンションの [**セット**] フォルダーや、 **[関数]** に表示される関数の関数グループフォルダーなど、選択したメンバーをコピーできない場合は、このオプションが無効になっていることにも注意してください。|  
|**[メンバーのフィルター選択]**|**[メンバーのフィルター選択]** ダイアログ ボックスを表示し、 **[メタデータ]** で選択した要素について表示されたメンバーをフィルター処理します。 **[メンバーのフィルター選択]** ダイアログ ボックスの詳細については、「[[メンバーのフィルター選択] ダイアログ ボックス &#40;Analysis Services - 多次元データ&#41;](filter-members-dialog-box-analysis-services-multidimensional-data.md)」を参照してください。<br /><br /> このオプションは、[**メタデータ**] が選択されている場合にのみ表示されることに注意してください。 また、このオプションは、属性のレベルが [**メタデータ**] で選択されている場合にのみ有効になることに注意してください。|  
|**Add Template**|選択したテンプレートに基づいて新しいアクション、ドリルスルー アクション、またはレポート アクションをキューブに追加し、それぞれ、 **アクション フォーム エディター**、 **ドリルスルー アクション フォーム エディター**、または **レポート アクション フォーム エディター**を表示します。<br /><br /> 注: このオプションは、[**メタデータ**] が選択されている場合にのみ表示されます。|  
  
## <a name="see-also"></a>参照  
 [MDX スクリプティングの基礎 &#40;Analysis Services&#41;](multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md)   
 [アクション &#40;キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](actions-cube-designer-analysis-services-multidimensional-data.md)   
 [ツールバーの [&#40;の操作] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](toolbar-actions-tab-cube-designer-analysis-services-multidimensional-data.md)   
 [アクション &#40;オーガナイザーの [アクション] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](action-organizer-cube-designer-analysis-services-multidimensional-data.md)   
 [アクションフォームエディター &#40;[アクション] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](action-form-editor-cube-designer-analysis-services-multidimensional-data.md)   
 [ドリルスルーアクションフォームエディター &#40;[アクション] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](drillthrough-action-form-editor-cube-designer-analysis-services-multidimensional-data.md)   
 [レポートアクションフォームエディター &#40;[アクション] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](report-action-form-editor-cube-designer-analysis-services-multidimensional-data.md)  
  
  
