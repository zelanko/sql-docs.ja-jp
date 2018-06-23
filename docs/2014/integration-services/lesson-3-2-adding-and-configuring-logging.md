---
title: 手順 2:ログ機能の追加と設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 56105f3f-e500-4669-8c8e-acf434527727
caps.latest.revision: 22
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 4d0bd778d04b00c2d90da3cd6a77ca1bf8f9c830
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36072362"
---
# <a name="step-2-adding-and-configuring-logging"></a>手順 2:ログ機能の追加と設定
  ここでは、Lesson 3.dtsx パッケージのデータ フローのログを有効にします。 次に、PipelineExecutionPlan イベントと PipelineExecuteTrees イベントを記録するテキスト ファイル ログ プロバイダーを構成します。 テキスト ファイル ログ プロバイダーは、表示や移行が容易なログを作成します。 パッケージの基本テスト段階では、この簡潔なログ ファイルは特に便利です。 ログ エントリは、 [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーの [ログ イベント] ウィンドウでも確認できます。  
  
### <a name="to-add-logging-to-the-package"></a>パッケージにログ機能を追加するには  
  
1.  次に、 **[SSIS]** メニューの **[ログ記録]** をクリックします。  
  
2.  **[SSIS ログの構成]** ダイアログ ボックスの **[コンテナー]** ペインで、一番上のパッケージ オブジェクト (Lesson 3) が選択されていることを確認します。  
  
3.  **[プロバイダーとログ]** タブで、 **[プロバイダーの種類]** ボックスの一覧から **[テキスト ファイルの SSIS ログ プロバイダー]** を選択し、 **[追加]** をクリックします。  
  
     新しいテキスト ファイル ログ プロバイダーがパッケージに追加されます。このプロバイダーの既定の名前は " **テキスト ファイルの SSIS ログ プロバイダー**" です。 次に、この新しいログ プロバイダーを構成します。  
  
4.  **名前**列に「`Lesson 3 Log File`です。  
  
5.  必要に応じて、 **[説明]** の内容を修正します。  
  
6.  **構成**列で、をクリックして**\<新しい接続 >** ログ情報の書き込み先となる先を指定します。  
  
     **[ファイル接続マネージャー エディター]** ダイアログ ボックスで、 **[使用法の種類]** ボックスの一覧から **[ファイルの作成]** を選択し、 **[参照]** をクリックします。 既定では、 **[ファイルの選択]** ダイアログ ボックスにこのプロジェクトのフォルダーが表示されますが、ログ情報を別の場所に保存することもできます。  
  
7.  **ファイルの選択** ダイアログ ボックスで、**ファイル名**ボックスに「 `TutorialLog.log`、 をクリック**開く**です。  
  
8.  **[OK]** をクリックして、 **[ファイル接続マネージャー エディター]** ダイアログ ボックスを閉じます。  
  
9. **[コンテナー]** ペインで、パッケージ コンテナー階層のすべてのノードを展開します。次に、 **[Extract Sample Currency Data]** チェック ボックスも含めすべてのチェック ボックスをオフにします。 次に、このノードのイベントのみを取得するため、 **[Extract Sample Currency Data]** チェック ボックスをオンにします。  
  
    > [!IMPORTANT]  
    >  **[Extract Sample Currency Data]** チェック ボックスがオフの状態で淡色表示になっている場合は、親コンテナーのログ設定が使用され、この作業用にログ イベントを有効にすることはできません。  
  
10. **[詳細]** タブの **[イベント]** 列で、 **[PipelineExecutionPlan]** イベントと **[PipelineExecutionTrees]** イベントのチェック ボックスをオンにします。  
  
11. **[詳細設定]** をクリックし、各イベントについて書き込まれるログ情報の詳細を確認します。 既定では、指定したイベントについて、すべての情報カテゴリが自動的に選択されます。  
  
12. **[標準]** をクリックして、情報カテゴリを非表示にします。  
  
13. **プロバイダーとログ** タブで、**名前**列で、選択`Lesson 3 Log File`です。 目的のパッケージのログ プロバイダーを作成したら、必要に応じてログの記録を一時的にオフにすることができます。ログ プロバイダーを削除したり、再作成する必要はありません。  
  
14. **[OK]** をクリックします。  
  
## <a name="next-steps"></a>次の手順  
 [手順 3: レッスン 3 のチュートリアル パッケージのテスト](../integration-services/lesson-3-3-testing-the-lesson-3-tutorial-package.md)  
  
  