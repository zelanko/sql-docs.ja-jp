---
title: '手順 5: フラット ファイル ソースの追加と構成 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5c95ce51-e0fe-4fc5-95eb-2945929f2b13
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f1f50c3aed4429a3ba05a23a969d050c45778c34
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85435849"
---
# <a name="step-5-adding-and-configuring-the-flat-file-source"></a>手順 5:フラット ファイル ソースの追加と構成
  ここでは、フラット ファイル ソースをパッケージに追加し、構成します。 フラット ファイル ソースとは、フラット ファイル接続マネージャーにより定義されるメタデータを使用するデータ フロー コンポーネントです。フラット ファイル接続マネージャーは、変換処理によってフラット ファイルから取得されるデータの形式や構造を指定します。 フラット ファイル接続マネージャーに定義されているファイル形式を使用し、1 つのフラット ファイルからデータを取得するよう、フラット ファイル ソースを定義できます。  
  
 このチュートリアルでは、前に作成した接続マネージャーを使用するようにフラットファイルソースを構成し `Sample Flat File Source Data` ます。  
  
### <a name="to-add-a-flat-file-source-component"></a>フラット ファイル ソース コンポーネントを追加するには  
  
1.  **データフローデザイナーを**開きます。そのためには、データフロータスクをダブルクリックするか、[ `Extract Sample Currency Data` **データフロー] タブ**をクリックします。  
  
2.  **[SSIS ツールボックス]** で **[その他の変換元]** を展開し、 **[フラット ファイル ソース]** を **[データ フロー]** タブのデザイン画面にドラッグします。  
  
3.  [**データフロー** ] デザイン画面で、新しく追加した**フラットファイルソース**を右クリックし **、[名前の変更]** をクリックして、名前をに変更し `Extract Sample Currency Data` ます。  
  
4.  このフラット ファイル ソースをダブルクリックして、[フラット ファイル ソース エディター] ダイアログ ボックスを開きます。  
  
5.  [**フラットファイル接続マネージャー** ] ボックスで、を選択し `Sample Flat File Source Data` ます。  
  
6.  **[列]** をクリックし、列名が正しいことを確認します。  
  
7.  **[OK]** をクリックします。  
  
8.  [フラット ファイル ソース] を右クリックし、 **[プロパティ]** をクリックします。  
  
9. [プロパティウィンドウで、 `LocaleID` プロパティが**英語 (米国)** に設定されていることを確認します。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [手順 6:参照変換の追加と構成](lesson-1-6-adding-and-configuring-the-lookup-transformations.md)  
  
## <a name="see-also"></a>関連項目  
 [フラットファイルソース](data-flow/flat-file-source.md)   
 [[フラット ファイル接続マネージャー エディター] &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md)  
  
  
