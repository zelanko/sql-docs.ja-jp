---
title: '手順 4: パッケージへのデータ フロー タスクの追加 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 96af3073-8f11-4444-b934-fe8613a2d084
caps.latest.revision: 21
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 29c42e491c6d36c20073a801051d8861d03ab0f6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36174537"
---
# <a name="step-4-adding-a-data-flow-task-to-the-package"></a>手順 4: パッケージへのデータ フロー タスクの追加
  前の実習では、データ ソースおよび変換先データに接続するための接続マネージャーを作成しました。次の実習では、パッケージにデータ フロー タスクを追加します。 データ フロー タスクには、変換元と変換先の間でデータを移動させるデータ フロー エンジンがカプセル化されており、データを移動する際に、変換、クリーン、修正を行うことができます。 抽出、変換、読み込み (ETL) プロセスのほとんどが、このデータ フロー タスクで実行されます。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] では、データ フローと制御フローが切り離されています。  
  
### <a name="to-add-a-data-flow-task"></a>データ フロー タスクを追加するには  
  
1.  **[制御フロー]** タブをクリックします。  
  
2.  **[SSIS ツールボックス]** で **[お気に入り]** を展開し、 **[データ フロー タスク]** を **[制御フロー]** タブのデザイン画面上にドラッグします。  
  
    > [!NOTE]  
    >  [SSIS ツールボックス] が表示されていない場合は、メイン メニューの [SSIS]、[SSIS ツールボックス] を選択し、SSIS ツールボックスを表示します。  
  
3.  **制御フロー**デザイン画面で、新しく追加したを右クリックし**Data Flow Task**、 をクリックして**の名前を変更**、名前を変更し、`Extract Sample Currency Data`です。  
  
     デザイン画面に追加するすべてのコンポーネントに一意な名前を付けるようにしましょう。 使いやすさと管理しやすさを考慮し、各コンポーネントの機能がわかるような名前を付けます。 このような方法で名前を付けておけば、自己文書化された [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージを作成できます。 パッケージを文書化するには、注釈を使用する方法もあります。 注釈の詳細については、「 [パッケージで注釈を使用する](use-annotations-in-packages.md)」を参照してください。  
  
4.  データ フロー タスクを右クリックし、をクリックして**プロパティ**、[プロパティ] ウィンドウであることを確認し、`LocaleID`プロパティに設定されている**英語 (米国)** です。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [手順 5: フラット ファイル ソースの追加と構成](lesson-1-5-adding-and-configuring-the-flat-file-source.md)  
  
## <a name="see-also"></a>参照  
 [データ フロー タスク](control-flow/data-flow-task.md)  
  
  