---
title: オプション (テキスト エディターに XML が書式設定 ページ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Formatting
ms.assetid: 97373178-d288-4127-af37-d9f5fe1b8607
caps.latest.revision: 12
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 667b01cbdaa1e5107dcbac8a68879a94d6efc06e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37209592"
---
# <a name="options-text-editor---xml---formatting-page"></a>[オプション] ([テキスト エディター]/[XML]/[書式設定] ページ)
  このダイアログ ボックスでは、XML エディターの書式設定を指定できます。 **[ツール]** メニューから **[オプション]** ダイアログ ボックスにアクセスできます。  
  
> [!NOTE]  
>  次の設定は、**[テキスト エディター]** フォルダーを展開し、**[XML]** フォルダーを展開して、**[オプション]** ダイアログ ボックスの **[書式設定]** オプションを選択したときに利用可能になります。  
  
## <a name="attributes"></a>属性  
 **手動による属性の書式設定を保持します。**  
 属性の書式設定を変更しません。 既定値です。  
  
> [!NOTE]  
>  属性が複数行にある場合、エディターは属性の各行にインデントを設定して、親要素のインデントに一致させます。  
  
 **別の行に属性を配置します。**  
 2 番目以降の属性を縦に配置して、最初の属性のインデントに一致させます。 次の XML テキストは、属性を配置する方法の例です。  
  
```  
<item id = "123-A"  
      name = "hammer"  
      price = "9.95"  
</item>  
```  
  
## <a name="auto-reformat"></a>[自動再フォーマット]  
 **クリップボードから貼り付けします。**  
 クリップボードから貼り付けられる XML テキストの書式設定を変更します。  
  
 **終了タグの完了時に**  
 終了タグが完了するときに、要素の書式設定を変更します。  
  
## <a name="mixed-content"></a>[混合コンテンツ]  
 **既定では、混合コンテンツを書式設定します。**  
 コンテンツが `xml:space="preserve"` 範囲内で検出された場合以外は、混合コンテンツの書式設定を変更します。 既定値です。  
  
 要素にテキストとマークアップが混在している場合、コンテンツは混合コンテンツと見なされます。 次に、混合コンテンツを含む要素の例を示します。  
  
```  
<dir>c:\data\AlphaProject\  
  <file readOnly="false">test1.txt</file>  
  <file readOnly="false">test2.txt</file>  
```  
  
 \</dir >  
  
## <a name="see-also"></a>参照  
 [XML エディター &#40;SQL Server Management Studio&#41;](../ssms/sql-server-management-studio-ssms.md)  
  
  
