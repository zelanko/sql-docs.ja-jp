---
title: '作業 17: SSIS パッケージによって作成された DQS クレンジングプロジェクトを確認する |Microsoft Docs'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: fc6cc258-72f5-4593-8edb-9f5bc66de9db
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 285eae7ea20d5919fa73bd0d514c755fe73d9de0
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "65484709"
---
# <a name="task-17-reviewing-dqs-cleansing-project-created-by-the-ssis-package"></a>タスク 17: SSIS パッケージによって作成された DQS クレンジング プロジェクトを確認する
  ここでは、DQS クライアントで SSIS パッケージにより作成された DQS プロジェクトを開き、クレンジング プロセスの結果を確認し、必要に応じてインタラクティブなクレンジングを実行し、結果をエクスポートします。  
  
1.  **Data Quality Client**を起動します。  
  
2.  [**管理**] ウィンドウで [**アクティビティの監視**] をクリックします。  
  
3.  **アクティビティの開始時刻**に基づいて一覧を並べ替え、最新のレコードを確認します。  
  
4.  プロジェクトの名前が次の形式で表示されていることに注意してください: **Cleansupplier Data. GUID**。  
  
     ![SSIS パッケージによって作成された DQS クレンジング プロジェクト](../../2014/tutorials/media/et-reviewingdqscpcreatedbythessispackage.jpg "SSIS パッケージによって作成された DQS クレンジング プロジェクト")  
  
5.  [**アクティブ**] フィールドの値が [**アクティブ**] になっていることに注意してください。  
  
6.  下のペインの [**プロファイラー** ] タブをクリックすると、SSIS パッケージによって実行されたクレンジングアクティビティのプロファイラーの統計情報が表示されます。  
  
7.  [**閉じる**] をクリックして、**管理**画面を閉じます。  
  
8.  **DQS クライアント**のメインページで、[**データ品質プロジェクト**] ペインの [**データ品質プロジェクトを開く**] をクリックします。  
  
9. プロジェクトの一覧で、SSIS DQS クレンジング コンポーネントによって作成されたプロジェクトを選択します。 プロジェクトの名前は、次の形式で指定する必要があります: **Cleanseandcurate。 (赤)**。 [**作成日**] 列に基づいて一覧を並べ替え、最新のレコードを検索することが必要になる場合があります。  
  
10. **[次へ]** をクリックします。  
  
11. [**結果の管理と表示**] ページは、このチュートリアルの前の手順で行った対話型のクレンジングから理解している必要があります。  
  
12. クレンジングの結果を確認します。 また、インタラクティブなクレンジングを実行し、Excel ファイルや次のページのデータベースに結果をエクスポートできます。  
  
13. **[次へ]** をクリックします。 この**エクスポート**ページでは、excel ファイル、CSV ファイル、または SQL データベースに結果をエクスポートできます。  
  
14. [**完了**] をクリックして活動を終了します。  
  
15. **DQS クライアント**のメインページで、[**管理**] ウィンドウの [**アクティビティの監視**] をクリックします。  
  
16. プロジェクトの**IsActive**フィールドの値が [**終了**] になっていることに注意してください。  
  
## <a name="next-step"></a>次の手順  
 [まとめ](../../2014/tutorials/conclusion.md)  
  
  
