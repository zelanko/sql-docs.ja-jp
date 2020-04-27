---
title: '[属性データの翻訳] ダイアログボックス (Analysis Services-多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensiondesigner.dimensionstoragesettings.f1
helpviewer_keywords:
- Attribute Data Translation dialog box
ms.assetid: bed286de-1e9b-49de-b09e-3cd076aba152
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2304f664178ab1f5d3718cccdcb4b1775a72948e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66063065"
---
# <a name="attribute-data-translation-dialog-box-analysis-services---multidimensional-data"></a>[属性データの翻訳] ダイアログ ボックス (Analysis Services - 多次元データ)
  **[属性データの翻訳]** ダイアログ ボックスを使用すると、翻訳キャプション データを含んでいる列を設定でき、翻訳済みデータと共に使用する照合順序と並べ替え順も設定できます。 **[属性データの翻訳]** ダイアログ ボックスを表示するには、次の手順に従います。  
  
-   **ディメンション デザイナー** の **[翻訳]** タブの **[ツール バー]** ペインで **[新しいキャプション列]** または **[キャプション列の編集]** をクリックします。  
  
-   **ディメンション デザイナー** の **[翻訳]** タブの翻訳の **詳細ペイン** を右クリックし、 **[新しいキャプション列]** または **[キャプション列の編集]** をクリックします。  
  
## <a name="options"></a>オプション  
 **属性**  
 選択した属性を表示します。  
  
 **Language**  
 選択した言語を表示します。  
  
 **[キャプションの翻訳]**  
 選択した属性の現在翻訳されているキャプションを設定します。  
  
 **[翻訳列]**  
 翻訳キャプション データが格納されている列を設定します。 1 つの列のみを選択できます。 プライマリ ディメンション テーブルによって参照されるすべての関連するテーブルが表示されます。  
  
 **[照合順序指定子]**  
 選択した属性の照合順序指定子を設定します。 既定では、現在の Windows 照合順序が選択されています。 下矢印をクリックして、使用可能な照合順序から選択します。  
  
 **Binary**  
 このオプションを選択すると、文字ごとに定義されたビット パターンに基づいてデータの並べ替えと比較を行います。 バイナリの並べ替え順では大文字と小文字が区別されるため、小文字は大文字より前に配置されます。また、アクセントも区別されます。 これは、最速の並べ替え順です。  
  
 このオプションが選択されていない場合、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] には関連する言語またはアルファベットの辞書で定義されている並べ替えおよび比較ルールが使用されます。  
  
> [!NOTE]  
>  このオプションが選択されている場合、 **[大文字と小文字を区別する]**、 **[アクセントを区別する]**、 **[かなを区別する]**、および **[文字幅を区別する]** オプションは無効になります。  
  
 **大文字と小文字を区別する**  
 このオプションを選択すると、関連する言語またはアルファベットに適用される辞書のルールに基づいてデータの並べ替えと比較を行い、大文字と小文字による区別を行います。  
  
 このオプションが選択されていない場合、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] は大文字と小文字を区別しません。 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]大文字と小文字を区別するかどうかは、大文字小文字を**区別**するかどうかを定義しません。  
  
 **アクセントを区別する**  
 このオプションを選択すると、関連する言語またはアルファベットに適用される辞書のルールに基づいてデータの並べ替えと比較を行い、アクセント符号が付いた文字と付いていない文字を区別します。 たとえば、'a' と '&#xE1;' は等しくありません。  
  
 このオプションが選択されていない場合、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] はアクセント符号の付いた文字と付いていない文字を同じものと見なします。  
  
 **[かなを区別する]**  
 このオプションを選択して、関連する言語またはアルファベットに適用される辞書のルールに基づいてデータの並べ替えと比較を行い、ひらがなとカタカナという日本語の 2 種類のかな文字を区別します。  
  
 このオプションが選択されていない場合、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] はひらがなとカタカナを同じものと見なします。  
  
 **[文字幅を区別する]**  
 このオプションを選択すると、関連する言語またはアルファベットに適用される辞書のルールに基づいてデータの並べ替えと比較を行い、1 バイト文字 (半角文字) と同じ文字の 2 バイト表現 (全角文字) とを区別します。  
  
 このオプションが選択されていない場合、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] は同じ文字の 1 バイト表現と 2 バイト表現を同じものと見なします。  
  
## <a name="see-also"></a>参照  
 [多次元データ &#40;Analysis Services のデザイナーとダイアログボックス&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [翻訳の詳細 &#40;翻訳] タブ、ディメンションデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](translation-details-dimension-designer-analysis-services-multidimensional-data.md)  
  
  
