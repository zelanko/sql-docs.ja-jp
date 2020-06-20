---
title: '手順 9: レッスン 1 のチュートリアル パッケージのテスト | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 9aee7acf-797b-46f2-830d-80ab64a9f0b6
author: janinezhang
ms.author: janinez
ms.openlocfilehash: fb4558d092daffc4a043d05b53a2d669f9cd66f1
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84966102"
---
# <a name="step-9-testing-the-lesson-1-tutorial-package"></a>手順 9:レッスン 1 のチュートリアル パッケージのテスト
  このレッスンでは次の作業を行いました。  
  
-   新しい [!INCLUDE[ssIS](../includes/ssis-md.md)] プロジェクトを作成しました。  
  
-   ソース データおよび変換先データに接続するための接続マネージャーをパッケージに追加し、構成しました。  
  
-   フラット ファイル ソースからデータを取得し、そのデータに対して必要な参照変換を実行した後、変換先に合わせてデータを構成するためのデータ フローを追加しました。  
  
 これでパッケージは完成です。 次に、パッケージをテストします。  
  
## <a name="checking-the-package-layout"></a>パッケージ レイアウトの確認  
 パッケージをテストする前に、次の図に示すオブジェクトがレッスン 1 のパッケージの制御フローとデータ フローに含まれていることを確認します。  
  
 **制御フロー**  
  
 ![パッケージ内の制御フロー](../../2014/tutorials/media/task9lesson1control.gif "パッケージ内の制御フロー")  
  
 **データ フロー**  
  
 ![パッケージ内のデータ フロー](../../2014/tutorials/media/task9lesson1data.gif "パッケージ内のデータ フロー")  
  
### <a name="to-run-the-lesson-1-tutorial-package"></a>レッスン 1 のチュートリアル パッケージを実行するには  
  
1.  **[デバッグ]** メニューの **[デバッグの開始]** をクリックします。  
  
     パッケージが実行されます。その結果、 **AdventureWorksDW2012** の **FactCurrency**ファクト テーブルに 1,097 個の行が追加されます。  
  
2.  パッケージの実行が完了したら、 **[デバッグ]** メニューの **[デバッグの停止]** をクリックします。  
  
## <a name="next-lesson"></a>次のレッスン  
 [レッスン 2: ループの追加](../integration-services/lesson-2-adding-looping-with-ssis.md)  
  
## <a name="see-also"></a>参照  
 [プロジェクトとパッケージの実行](packages/run-integration-services-ssis-packages.md)  
  
  
