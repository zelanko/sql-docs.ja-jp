---
title: 手順 3:レッスン 6 のパッケージをテストする | Microsoft Docs
ms.custom: ''
ms.date: 01/11/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: c184c92d-948f-4037-a502-5fabd909c84c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 001ba5fc56393cbbcdbc8b5379abc8390dc05e0a
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/16/2019
ms.locfileid: "65721239"
---
# <a name="lesson-6-3-test-the-lesson-6-package"></a>レッスン 6-3:レッスン 6 のパッケージをテストする

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


パッケージを実行すると、**VarFolderName** パラメーターから **Directory** プロパティの値が取得されます。  
  
パッケージによって **Directory** プロパティが更新されることを確認するには、パッケージを実行します。 新しいディレクトリにはサンプル データ ファイルを 3 つコピーしたため、データ フローは 3 回実行されます。
  
## <a name="check-the-package-layout"></a>パッケージ レイアウトを確認する  
パッケージをテストする前に、レッスン 6 の制御フローとデータ フローが次の図にあるオブジェクトと同様であることを確認します。   
  
**制御フロー**  
  
![制御フロー](../integration-services/media/task4lesson2control.gif "制御フロー")  
  
**データ フロー**  
  
![データ フロー](../integration-services/media/task5lesson5data.gif "データ フロー")  
  
## <a name="test-the-lesson-6-package"></a>レッスン 6 のパッケージをテストする  
  
1.  **[デバッグ]** メニューの **[デバッグの開始]** を選択します。  
  
2.  パッケージの実行が完了したら、**[デバッグ]** メニューの **[デバッグの停止]** を選択します。  
  
## <a name="go-to-next-task"></a>次のタスクに進む
[手順 4:レッスン 6 のパッケージを配置する](../integration-services/lesson-6-4-deploying-the-lesson-6-package.md)  
  
  
  
