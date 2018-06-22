---
title: Microsoft Excel ファイル (SSAS) への接続 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.bidtoolset.connexcelfile.f1
ms.assetid: 126f7d6b-d270-40e7-b23e-8d114f87065b
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 48de9fd006c3918a23227a097743a95e138b577e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36083310"
---
# <a name="connect-to-a-microsoft-excel-file-ssas"></a>[Microsoft Excel ファイルへの接続] (SSAS)
  **テーブルのインポート ウィザード**のこのページを使用すると、ローカル コンピューターに保存されている Microsoft Excel ファイルに接続できます。 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]からウィザードにアクセスするには、 **[モデル]** メニューの **[データ ソースからのインポート]** をクリックします。  
  
 Microsoft Excel ファイルに接続するには、適切な ACE プロバイダーがコンピューターにインストールされている必要があります。 詳細については、「[サポートされているデータ ソース (SSAS テーブル)](tabular-models/data-sources-supported-ssas-tabular.md)」を参照してください。  
  
> [!NOTE]  
>  このページでファイルを選択する際には、現在のユーザーの資格情報が使用されます。 ただし、[権限借用情報] ページで指定されたユーザーに、選択したファイルの読み取り権限がないと、インポートは成功しません。  
  
## <a name="uielement-list"></a>UI 要素の一覧  
 **接続の表示名**  
 このデータ ソース接続の一意の名前を入力します。 このフィールドは必須です。  
  
 **Excel ファイル パス**  
 Excel ファイルの完全なパスを指定します。  
  
 **[参照]**  
 使用可能な Excel ファイルがある場所に移動します。  
  
 **詳細設定**  
 **[詳細プロパティの設定]** ダイアログ ボックスを使用して追加の接続プロパティを設定します。  
  
 **最初の行を列見出しとして使用します。**  
 先頭のデータ行を目的のテーブルの列見出しとして使用するかどうかを指定します。  
  
 **[接続テスト]**  
 現在の設定を使用して、データ ソースに対する接続の確立を試みます。 接続が正常に確立されたかどうかを示すメッセージが表示されます。  
  
  