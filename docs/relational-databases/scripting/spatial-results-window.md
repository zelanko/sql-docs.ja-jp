---
title: "[空間結果] ウィンドウ | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2d5a477-6496-4d01-adee-7322ebdfadf3
caps.latest.revision: 8
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 66e1a9e14b4a786e6ca45a9ab0e761975563c415
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="spatial-results-window"></a>[空間結果] ウィンドウ
  **[空間結果]** ウィンドウには、空間データを表示するための視覚的なマッピング ツールが用意されています。 空間結果を表示するには、geometry 型または geography 型のデータを含む空間列がクエリ結果に含まれている必要があります。  
  
> [!NOTE]  
>  **[空間結果]** ウィンドウを使用できるのは、 **[結果]** ウィンドウ内のグリッドに結果が返される場合だけです。 結果がテキストとして返されるように設定すると、このウィンドウは使用できません。  
  
## <a name="options"></a>オプション  
 **[空間列の選択]**  
 クエリ結果の空間列から、表示する空間列を指定します。 列は、一度に 1 つしか選択できません。  
  
 **[ラベル列の選択]**  
 クエリ結果に返された列から、空間データにラベルを付けるための空間列以外の列を指定します。 列は、一度に 1 つしか選択できません。  
  
 クエリで Point インスタンスのみが返される場合は、このオプションを使用できません。  
  
 **[投影の選択]**  
 geography 型のデータを、正距円筒図法、メルカトル図法、ロビンソン図法、ボンヌ図法という 4 つの投影法のいずれかで表示します。  
  
 このオプションは、geometry 型のデータには使用できません。  
  
 **[ズーム]**  
 指数スケール上でマップの表示を調整します。  
  
 **[グリッド線の表示]**  
 座標グリッド線の表示と非表示を切り替えます。  
  
 多角形の場合、ラベルが表示されるのは、図形がラベルのテキストを保持するのに十分な大きさの場合だけです。 小さい図形にラベルを表示するには、ズームを調整します。  
  
> [!NOTE]  
>  Point インスタンスにラベルを付けることはできません。  
  
## <a name="see-also"></a>参照  
 [オブジェクト エクスプローラーでの空間データの表示](../../relational-databases/scripting/view-spatial-data-in-object-explorer.md)   
 [空間データ &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)   
 [データベース エンジン クエリ エディター &#40;SQL Server Management Studio&#41;](../../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md)   
 [クエリおよびテキスト エディター &#40;SQL Server Management Studio&#41;](../../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md)  
  
  
