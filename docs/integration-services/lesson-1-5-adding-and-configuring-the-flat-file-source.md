---
title: "手順 5: の追加と構成、フラット ファイル ソース |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 5c95ce51-e0fe-4fc5-95eb-2945929f2b13
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 2c56b634f36e69e06e03e0206cd70d841f4682ea
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="lesson-1-5---adding-and-configuring-the-flat-file-source"></a>レッスン 1 ~ 5 を追加して、フラット ファイル ソースを構成します。
ここでは、フラット ファイル ソースをパッケージに追加し、構成します。 フラット ファイル ソースとは、フラット ファイル接続マネージャーにより定義されるメタデータを使用するデータ フロー コンポーネントです。フラット ファイル接続マネージャーは、変換処理によってフラット ファイルから取得されるデータの形式や構造を指定します。 フラット ファイル接続マネージャーに定義されているファイル形式を使用し、1 つのフラット ファイルからデータを取得するよう、フラット ファイル ソースを定義できます。  
  
このチュートリアルでは、以前に作成した **Sample Flat File Source Data** 接続マネージャーを使用するように、フラット ファイル ソースを構成します。  
  
### <a name="to-add-a-flat-file-source-component"></a>フラット ファイル ソース コンポーネントを追加するには  
  
1.  **[Extract Sample Currency Data]** データ フローをダブルクリックするか、 **[データ フロー]** タブをクリックし、 **[データ フロー]**デザイナーを開きます。  
  
2.  **[SSIS ツールボックス]**で **[その他の変換元]**を展開し、 **[フラット ファイル ソース]** を **[データ フロー]** タブのデザイン画面にドラッグします。  
  
3.  **[データ フロー]** デザイン画面で、新しく追加した **[フラット ファイル ソース]**を右クリックし、 **[名前の変更]**をクリックします。名前を「 **Extract Sample Currency Data**」に変更します。  
  
4.  このフラット ファイル ソースをダブルクリックして、[フラット ファイル ソース エディター] ダイアログ ボックスを開きます。  
  
5.  **[フラット ファイル接続マネージャー]** ボックスで " **Sample Flat File Source Data**" を選択します。  
  
6.  **[列]** をクリックし、列名が正しいことを確認します。  
  
7.  **[OK]**をクリックします。  
  
8.  [フラット ファイル ソース] を右クリックし、 **[プロパティ]**をクリックします。  
  
9. [プロパティ] ウィンドウで、 **LocaleID** プロパティが **[英語 (米国)]**に設定されていることを確認します。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
[手順 6 : 参照変換の追加と構成](../integration-services/lesson-1-6-adding-and-configuring-the-lookup-transformations.md)  
  
## <a name="see-also"></a>参照  
[[フラット ファイル ソース]](../integration-services/data-flow/flat-file-source.md)  
[[フラット ファイル接続マネージャー エディター] &#40;[全般] ページ&#41;](../integration-services/connection-manager/flat-file-connection-manager-editor-general-page.md)  
  
  
  

