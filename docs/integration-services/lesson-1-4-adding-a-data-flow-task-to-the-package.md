---
title: "手順 4: パッケージへのデータ フロー タスクの追加 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: tutorial
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to: SQL Server 2016
ms.assetid: 96af3073-8f11-4444-b934-fe8613a2d084
caps.latest.revision: "21"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: d67e1dc478ce982dc65ff7f0ed86ea3447395b84
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="lesson-1-4---adding-a-data-flow-task-to-the-package"></a>レッスン 1-4 - パッケージへのデータ フロー タスクの追加
前の実習では、データ ソースおよび変換先データに接続するための接続マネージャーを作成しました。次の実習では、パッケージにデータ フロー タスクを追加します。 データ フロー タスクには、変換元と変換先の間でデータを移動させるデータ フロー エンジンがカプセル化されており、データを移動する際に、変換、クリーン、修正を行うことができます。 抽出、変換、読み込み (ETL) プロセスのほとんどが、このデータ フロー タスクで実行されます。  
  
> [!NOTE]  
> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] では、データ フローと制御フローが切り離されています。  
  
### <a name="to-add-a-data-flow-task"></a>データ フロー タスクを追加するには  
  
1.  **[制御フロー]** タブをクリックします。  
  
2.  **[SSIS ツールボックス]**で **[お気に入り]**を展開し、 **[データ フロー タスク]** を **[制御フロー]** タブのデザイン画面上にドラッグします。  
  
    > [!NOTE]  
    > [SSIS ツールボックス] が表示されていない場合は、メイン メニューの [SSIS]、[SSIS ツールボックス] を選択し、SSIS ツールボックスを表示します。  
  
3.  **[制御フロー]** デザイン画面で、新しく追加した **[データ フロー タスク]**を右クリックし、 **[名前の変更]**をクリックします。新しい名前として「 **Extract Sample Currency Data**」と入力します。  
  
    デザイン画面に追加するすべてのコンポーネントに一意な名前を付けるようにしましょう。 使いやすさと管理しやすさを考慮し、各コンポーネントの機能がわかるような名前を付けます。 このような方法で名前を付けておけば、自己文書化された [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージを作成できます。 パッケージを文書化するには、注釈を使用する方法もあります。 注釈の詳細については、「 [パッケージで注釈を使用する](../integration-services/use-annotations-in-packages.md)」を参照してください。  
  
4.  [データ フロー タスク] を右クリックして **[プロパティ]**をクリックし、[プロパティ] ウィンドウで **LocaleID** プロパティが **[英語 (米国)]**に設定されていることを確認します。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
[手順 5: フラット ファイル ソースの追加と構成](../integration-services/lesson-1-5-adding-and-configuring-the-flat-file-source.md)  
  
## <a name="see-also"></a>参照  
[[データ フロー タスク]](../integration-services/control-flow/data-flow-task.md)  
  
  
  
