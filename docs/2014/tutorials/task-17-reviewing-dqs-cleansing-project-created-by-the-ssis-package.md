---
title: 'タスク 17: で DQS クレンジング プロジェクトの作成を確認して、SSIS パッケージ |Microsoft Docs'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: fc6cc258-72f5-4593-8edb-9f5bc66de9db
caps.latest.revision: 6
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 63d715ae86464a3d9411296fe8ffdfab155bab38
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37308842"
---
# <a name="task-17-reviewing-dqs-cleansing-project-created-by-the-ssis-package"></a>タスク 17: SSIS パッケージによって作成された DQS クレンジング プロジェクトを確認する
  ここでは、DQS クライアントで SSIS パッケージにより作成された DQS プロジェクトを開き、クレンジング プロセスの結果を確認し、必要に応じてインタラクティブなクレンジングを実行し、結果をエクスポートします。  
  
1.  起動**Data Quality Client**します。  
  
2.  クリックして**アクティビティの監視**で、**管理**ウィンドウ。  
  
3.  に基づいて一覧を並べ替える**アクティビティの開始時刻**を最新のレコードを参照してください。  
  
4.  次の形式でプロジェクトの名前が表示されるに注意してください: **CleanseAndCurate.Cleanse Supplier Data.GUID**します。  
  
     ![SSIS パッケージによって作成された DQS クレンジング プロジェクト](../../2014/tutorials/media/et-reviewingdqscpcreatedbythessispackage.jpg "SSIS パッケージによって作成された DQS クレンジング プロジェクト")  
  
5.  いることを確認の値、**アクティブ**フィールドは**Active**。  
  
6.  クリックして**Profiler**  タブで、下のペインに SSIS パッケージが実行したクレンジング アクティビティのプロファイラーの統計情報を参照してください。  
  
7.  クリックして**閉じます**を閉じる、**管理**画面。  
  
8.  メイン ページで**DQS クライアント**、 をクリックして**データ品質プロジェクトを開く**で、**データ品質プロジェクト**ウィンドウ。  
  
9. プロジェクトの一覧で、SSIS DQS クレンジング コンポーネントによって作成されたプロジェクトを選択します。 プロジェクトの名前を形式でなければなりません: **CleanseAndCurate.Cleanse Supplier Data.GUID (赤色)** します。 に基づいて一覧を並べ替える必要があります**作成された日付**列と最新のレコードを参照してください。  
  
10. **[次へ]** をクリックします。  
  
11. **管理し、結果を表示する**ページはインタラクティブなクレンジングのこのチュートリアルで前に行ったから理解する必要があります。  
  
12. クレンジングの結果を確認します。 また、インタラクティブなクレンジングを実行し、Excel ファイルや次のページのデータベースに結果をエクスポートできます。  
  
13. **[次へ]** をクリックします。 この**エクスポート** ページで、excel ファイル、CSV ファイル、または SQL database には、結果をエクスポートすることができます。  
  
14. クリックして**完了**してアクティビティを終了します。  
  
15. メイン ページで**DQS クライアント**、 をクリックして**アクティビティの監視**で、**管理**ウィンドウ。  
  
16. 注意の値**IsActive**フィールドは、プロジェクトが**終了**ようになりました。  
  
## <a name="next-step"></a>次の手順  
 [まとめ](../../2014/tutorials/conclusion.md)  
  
  
