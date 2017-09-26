---
title: "手順 9: レッスン 1 のチュートリアル パッケージのテスト |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 9aee7acf-797b-46f2-830d-80ab64a9f0b6
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: ca45e8e1ba02246eb5429bd7bfea125663f69f41
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="lesson-1-9---testing-the-lesson-1-tutorial-package"></a>レッスン 1 ~ 9、レッスン 1 のチュートリアル パッケージのテスト
このレッスンでは次の作業を行いました。  
  
-   新しい [!INCLUDE[ssIS](../includes/ssis-md.md)] プロジェクトを作成しました。  
  
-   ソース データおよび変換先データに接続するための接続マネージャーをパッケージに追加し、構成しました。  
  
-   フラット ファイル ソースからデータを取得し、そのデータに対して必要な参照変換を実行した後、変換先に合わせてデータを構成するためのデータ フローを追加しました。  
  
これでパッケージは完成です。 次に、パッケージをテストします。  
  
## <a name="checking-the-package-layout"></a>パッケージ レイアウトの確認  
パッケージをテストする前に、次の図に示すオブジェクトがレッスン 1 のパッケージの制御フローとデータ フローに含まれていることを確認します。  
  
**制御フロー**  
  
![パッケージ内のフローを制御](../integration-services/media/task9lesson1control.gif "パッケージ内のフロー制御")  
  
**データ フロー**  
  
![パッケージ内のデータ フロー](../integration-services/media/task9lesson1data.gif "パッケージ内のデータ フロー")  
  
### <a name="to-run-the-lesson-1-tutorial-package"></a>レッスン 1 のチュートリアル パッケージを実行するには  
  
1.  **[デバッグ]** メニューの **[デバッグの開始]**をクリックします。  
  
    パッケージが実行されます。その結果、 **AdventureWorksDW2012** の **FactCurrency**ファクト テーブルに 1,097 個の行が追加されます。  
  
2.  パッケージの実行が完了したら、 **[デバッグ]** メニューの **[デバッグの停止]**をクリックします。  
  
## <a name="next-lesson"></a>次のレッスン  
[レッスン 2: SSIS でのループの追加](../integration-services/lesson-2-adding-looping-with-ssis.md)  
  
## <a name="see-also"></a>参照  
[プロジェクトとパッケージの実行](https://msdn.microsoft.com/library/ms141708(v=sql.110).aspx) 
  
  
  

