---
title: 手順 9:レッスン 1 のチュートリアル パッケージのテスト | Microsoft Docs
ms.custom: ''
ms.date: 01/03/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 9aee7acf-797b-46f2-830d-80ab64a9f0b6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 13c24945715ca9b0fa1ebac06b66d777c4eadaea
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "86917323"
---
# <a name="lesson-1-9-test-the-lesson-1-package"></a>レッスン 1 から 9:レッスン 1 のパッケージをテストする

[!INCLUDE[sqlserver-ssis](../includes/applies-to-version/sqlserver-ssis.md)]



このチュートリアルでは、次の作業を行いました。  
  
-   新しい [!INCLUDE[ssIS](../includes/ssis-md.md)] プロジェクトを作成しました。  
  
-   ソース データおよび変換先データに接続するパッケージ用の接続マネージャーを構成しました。  
  
-   フラット ファイル ソースからデータを取得し、そのデータに対して必要な参照変換を実行した後、変換先に合わせてデータを構成するためのデータ フローを追加しました。  
  
これでパッケージは完成し、テストすることができます。
  
## <a name="check-the-package-components"></a>パッケージのコンポーネントの確認
  
パッケージをテストする前に、次の図に示すオブジェクトがレッスン 1 のパッケージの制御フローとデータ フローに含まれていることを確認します。  
  
**制御フロー** 
  
![パッケージ内の制御フロー](../integration-services/media/task9lesson1control.gif "パッケージ内の制御フロー")  
  
**データ フロー**  
  
![パッケージ内のデータ フロー](../integration-services/media/task9lesson1data.gif "パッケージ内のデータ フロー")  
  
## <a name="run-the-lesson-1-package"></a>レッスン 1 のパッケージの実行  
  
1.  **[デバッグ]** メニューの **[デバッグの開始]** を選択します。  
  
    パッケージが実行され、その結果、**AdventureWorksDW2012** の **NewFactCurrencyRate** ファクト テーブルに 1,097 行が正常に追加されます。 この結果を確認するには、 **[データ フロー]** タブを選択します。
  
2.  パッケージの実行が完了したら、 **[デバッグ]** メニューの **[デバッグの停止]** を選択します。  
  
## <a name="go-to-next-lesson"></a>次のレッスンに進む
[レッスン 2:SSIS でのループの追加](../integration-services/lesson-2-adding-looping-with-ssis.md)  
  
## <a name="see-also"></a>関連項目  
[プロジェクトとパッケージの実行](packages/run-integration-services-ssis-packages.md) 
  
  
  
