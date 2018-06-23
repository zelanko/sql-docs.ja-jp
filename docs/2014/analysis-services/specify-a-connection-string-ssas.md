---
title: 接続文字列 (SSAS) の指定 |Microsoft ドキュメント
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
- sql12.asvs.bidtoolset.speconnstring.f1
ms.assetid: 3f89b55b-2659-4e9f-a3ad-ab9a23b6942d
caps.latest.revision: 7
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: fc0988701ba21ef7e6880b85abab6309479a8a2f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36175822"
---
# <a name="specify-a-connection-string-ssas"></a>[接続文字列の指定] (SSAS)
  **テーブルのインポート ウィザード** のこのページを使用すると、OLE DB データ ソースまたは ODBC データ ソースに接続するための接続文字列を指定できます。 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]からウィザードにアクセスするには、 **[モデル]** メニューの **[データ ソースからのインポート]** をクリックします。  
  
 データ ソースに接続するには、適切なプロバイダーがコンピューターにインストールされている必要があります。 サポートされているデータ ソースおよびプロバイダーの詳細については、「[サポートされているデータ ソース (SSAS テーブル)](tabular-models/data-sources-supported-ssas-tabular.md)」を参照してください。  
  
## <a name="uielement-list"></a>UI 要素の一覧  
 **この接続のフレンドリ名**  
 このデータ ソース接続の一意の名前を入力します。 このフィールドは必須です。  
  
 **接続文字列**  
 OLE DB または ODBC データ ソースへの接続に使用する接続文字列を入力します。  
  
 **ビルド**  
 **[データ リンク プロパティ]** ダイアログ ボックスを使用して接続文字列のプロパティを指定します。 詳細については、Microsoft Data Link のヘルプを参照してください。このダイアログ ボックスから参照できます。  
  
 **[接続テスト]**  
 指定された接続文字列を使用して、データ ソースに対する接続の確立を試みます。 接続が正常に確立されたかどうかを示すメッセージが表示されます。  
  
  