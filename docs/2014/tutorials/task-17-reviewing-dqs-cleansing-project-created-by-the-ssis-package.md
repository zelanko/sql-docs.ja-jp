---
title: 'タスク 17: で DQS クレンジング プロジェクトの作成を確認、SSIS パッケージによって |Microsoft ドキュメント'
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
ms.topic: article
ms.assetid: fc6cc258-72f5-4593-8edb-9f5bc66de9db
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 4226fd9a8e8eb8aa2851eed8eb318b8535010c8a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36174836"
---
# <a name="task-17-reviewing-dqs-cleansing-project-created-by-the-ssis-package"></a>タスク 17: SSIS パッケージによって作成された DQS クレンジング プロジェクトを確認する
  ここでは、DQS クライアントで SSIS パッケージにより作成された DQS プロジェクトを開き、クレンジング プロセスの結果を確認し、必要に応じてインタラクティブなクレンジングを実行し、結果をエクスポートします。  
  
1.  起動**Data Quality Client**です。  
  
2.  をクリックして**アクティビティの監視**で、**管理**ウィンドウです。  
  
3.  基づく並べ替えの**アクティビティの開始時刻**を最新のレコードを確認します。  
  
4.  次の形式でプロジェクトの名前が表示されるに注意してください: **CleanseAndCurate.Cleanse Supplier Data.GUID**です。  
  
     ![SSIS パッケージによって作成された DQS クレンジング プロジェクト](../../2014/tutorials/media/et-reviewingdqscpcreatedbythessispackage.jpg "SSIS パッケージによって作成された DQS クレンジング プロジェクト")  
  
5.  注意しての値、**アクティブ**フィールドは**Active**です。  
  
6.  をクリックして**プロファイラー**  タブで、下部ペインに、SSIS パッケージを実行したクレンジング アクティビティに関するプロファイラーの統計情報を参照してください。  
  
7.  をクリックして**閉じる**を閉じる、**管理**画面。  
  
8.  メイン ページで**DQS クライアント**をクリックして**データ品質プロジェクトを開く**で、**データ品質プロジェクト**ウィンドウです。  
  
9. プロジェクトの一覧で、SSIS DQS クレンジング コンポーネントによって作成されたプロジェクトを選択します。 プロジェクトの名前が形式でなければなりません: **CleanseAndCurate.Cleanse Supplier Data.GUID (赤色)** です。 に基づいて一覧を並べ替える必要があります**作成された日付**列と最新のレコードを探します。  
  
10. **[次へ]** をクリックします。  
  
11. **管理と結果を表示する**ページは、インタラクティブなクレンジングでこのチュートリアルで先ほど行った理解する必要があります。  
  
12. クレンジングの結果を確認します。 また、インタラクティブなクレンジングを実行し、Excel ファイルや次のページのデータベースに結果をエクスポートできます。  
  
13. **[次へ]** をクリックします。 この**エクスポート** ページで、excel ファイル、CSV ファイル、または SQL データベースに結果をエクスポートすることができます。  
  
14. をクリックして**完了**アクティビティを終了します。  
  
15. メイン ページで**DQS クライアント**をクリックして**アクティビティの監視**で、**管理**ウィンドウです。  
  
16. 注意して、値の**IsActive**フィールドは、プロジェクトは**終了**ようになりました。  
  
## <a name="next-step"></a>次の手順  
 [まとめ](../../2014/tutorials/conclusion.md)  
  
  