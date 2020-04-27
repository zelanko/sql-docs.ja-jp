---
title: Microsoft Excel ファイルへの接続 (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connexcelfile.f1
ms.assetid: 126f7d6b-d270-40e7-b23e-8d114f87065b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3e49b37a6f344b7fc6c45c9767a05c7f7d5bfe6e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66087320"
---
# <a name="connect-to-a-microsoft-excel-file-ssas"></a>[Microsoft Excel ファイルへの接続] (SSAS)
  **テーブルのインポート ウィザード** のこのページを使用すると、ローカル コンピューターに保存されている Microsoft Excel ファイルに接続できます。 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]からウィザードにアクセスするには、 **[モデル]** メニューの **[データ ソースからのインポート]** をクリックします。  
  
 Microsoft Excel ファイルに接続するには、適切な ACE プロバイダーがコンピューターにインストールされている必要があります。 詳細については、「[サポートされているデータ ソース &#40;SSAS テーブル&#41;](tabular-models/data-sources-supported-ssas-tabular.md)」を参照してください。  
  
> [!NOTE]  
>  このページでファイルを選択する際には、現在のユーザーの資格情報が使用されます。 ただし、[権限借用情報] ページで指定されたユーザーに、選択したファイルの読み取り権限がないと、インポートは成功しません。  
  
## <a name="uielement-list"></a>UI 要素の一覧  
 **[接続の表示名]**  
 このデータ ソース接続の一意の名前を入力します。 これは必須フィールドです。  
  
 **Excel ファイルのパス**  
 Excel ファイルの完全なパスを指定します。  
  
 **参照**  
 使用可能な Excel ファイルがある場所に移動します。  
  
 **詳細設定**  
 **[詳細プロパティの設定**] ダイアログボックスを使用して、追加の接続プロパティを設定します。  
  
 **[先頭の行を列見出しとして使用する]**  
 先頭のデータ行を目的のテーブルの列見出しとして使用するかどうかを指定します。  
  
 **接続をテスト**  
 現在の設定を使用して、データ ソースに対する接続の確立を試みます。 接続が正常に確立されたかどうかを示すメッセージが表示されます。  
  
  
