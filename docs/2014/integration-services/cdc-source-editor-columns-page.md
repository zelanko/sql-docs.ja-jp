---
title: CDC ソース エディター (列 ページ) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.ssis.designer.cdcsource.columns.f1
ms.assetid: bcf3030e-98d8-4445-967c-33c3f8ecb4fc
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 87d5d9b1096e2068759a2100b4daf504849fba0e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36083231"
---
# <a name="cdc-source-editor-columns-page"></a>[CDC ソース エディター] ([列] ページ)
  **[CDC ソース エディター]** ダイアログ ボックスの **[列]** ページを使用すると、出力列をそれぞれの外部 (ソース) 列にマップできます。  
  
 CDC ソースの詳細については、「 [CDC Source](data-flow/cdc-source.md)」を参照してください。  
  
## <a name="task-list"></a>タスク一覧  
 **[CDC ソース エディター] の [列] ページを開くには**  
  
1.  [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]で、CDC ソースを含む [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] パッケージを開きます。  
  
2.  **[データ フロー]** タブで、CDC ソースをダブルクリックします。  
  
3.  **[CDC ソース エディター]** で、 **[列]** をクリックします。  
  
## <a name="options"></a>および  
 **使用できる外部列**  
 データ ソース内の使用できる外部列の一覧です。 このテーブルを使用して列を追加または削除することはできません。 ソースで使用する列を選択します。 選択した列は、選択した順序で **[外部列]** の一覧に追加されます。  
  
 **[外部列]**  
 外部 (ソース) 列のビューです。CDC ソースのデータを使用するコンポーネントを構成するときの表示順になります。 この順序を変更するには、まず **[使用できる外部列]** の一覧で選択した列を消去してから、別の順序で一覧から外部列を選択します。 選択した列は、選択した順序で **[外部列]** の一覧に追加されます。  
  
 **出力列**  
 各出力列の一意の名前を入力します。 既定では選択された外部 (ソース) 列の名前になりますが、一意でわかりやすい名前を付けることもできます。 入力した名前は、SSIS デザイナーで表示されます。  
  
## <a name="see-also"></a>参照  
 [[CDC ソース エディター&#40;接続マネージャー] ページ&#41;](../../2014/integration-services/cdc-source-editor-connection-manager-page.md)   
 [[CDC ソース エディター&#40;エラー出力] ページ&#41;](../../2014/integration-services/cdc-source-editor-error-output-page.md)  
  
  