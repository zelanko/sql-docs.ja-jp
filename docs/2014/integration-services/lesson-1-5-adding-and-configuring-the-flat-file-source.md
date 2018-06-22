---
title: '手順 5: フラット ファイル ソースの追加と構成 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5c95ce51-e0fe-4fc5-95eb-2945929f2b13
caps.latest.revision: 20
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: a48d451248e28f8c9e0fd623c96022f558b80ca8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36084352"
---
# <a name="step-5-adding-and-configuring-the-flat-file-source"></a>手順 5: フラット ファイル ソースの追加と構成
  ここでは、フラット ファイル ソースをパッケージに追加し、構成します。 フラット ファイル ソースとは、フラット ファイル接続マネージャーにより定義されるメタデータを使用するデータ フロー コンポーネントです。フラット ファイル接続マネージャーは、変換処理によってフラット ファイルから取得されるデータの形式や構造を指定します。 フラット ファイル接続マネージャーに定義されているファイル形式を使用し、1 つのフラット ファイルからデータを取得するよう、フラット ファイル ソースを定義できます。  
  
 このチュートリアルでは、使用するフラット ファイル ソースを構成する、`Sample Flat File Source Data`以前に作成した接続マネージャーです。  
  
### <a name="to-add-a-flat-file-source-component"></a>フラット ファイル ソース コンポーネントを追加するには  
  
1.  開いている、**データ フロー**をダブルクリックするか、デザイナー、`Extract Sample Currency Data`データ フロー タスクをクリックして、**データ フロー タブ**です。  
  
2.  **[SSIS ツールボックス]** で **[その他の変換元]** を展開し、 **[フラット ファイル ソース]** を **[データ フロー]** タブのデザイン画面にドラッグします。  
  
3.  **データ フロー**デザイン画面で、新しく追加したを右クリックして**フラット ファイル ソース**、 をクリックして**の名前を変更**、名前を変更し、`Extract Sample Currency Data`です。  
  
4.  このフラット ファイル ソースをダブルクリックして、[フラット ファイル ソース エディター] ダイアログ ボックスを開きます。  
  
5.  **フラット ファイル接続マネージャー**ボックスで、`Sample Flat File Source Data`です。  
  
6.  **[列]** をクリックし、列名が正しいことを確認します。  
  
7.  **[OK]** をクリックします。  
  
8.  [フラット ファイル ソース] を右クリックし、 **[プロパティ]** をクリックします。  
  
9. [プロパティ] ウィンドウであることを確認、`LocaleID`プロパティに設定されている**英語 (米国)** です。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [手順 6: 参照変換の追加と構成](lesson-1-6-adding-and-configuring-the-lookup-transformations.md)  
  
## <a name="see-also"></a>参照  
 [フラット ファイル ソース](data-flow/flat-file-source.md)   
 [[フラット ファイル接続マネージャー エディター] &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md)  
  
  