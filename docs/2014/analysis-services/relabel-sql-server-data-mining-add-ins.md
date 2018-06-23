---
title: ラベルの変更 (SQL Server データ マイニング アドイン) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data preparation
- relabel
- data cleaning
ms.assetid: af041b39-fdd1-4cb5-a5ef-2f3ddab84614
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 50dd1a2c4cd425243c55ef9181387a08c5d935ba
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36174806"
---
# <a name="relabel-sql-server-data-mining-add-ins"></a>ラベルの変更 (SQL Server データ マイニング アドイン)
  ![ラベルの変更ツールの office 13 アイコン](media/dm13-relabel.gif "ラベルの変更ツールの Office 13 アイコン")  
  
 Excel 用のデータ マイニング クライアントでは、データの新しいラベルを作成して、分析結果を理解しやすくできます。  
  
 ラベルを変更する理由は次のとおりです。  
  
-   データがコード化された結果を含んでいる場合 (たとえば 1 は男性、2 は女性など)。  
  
-   バケット化した数値の範囲に、わかりやすい名前を付ける場合。  
  
-   長い名前を簡単にする場合。  
  
## <a name="using-the-relabel-wizard"></a>ラベルの変更ウィザードの使用  
  
1.  **データ マイニング**リボンで、をクリックして**クリーン**し、**ラベルの変更**です。  
  
2.  Select the table or data range that has the data you want to fix.修正するデータが含まれているテーブルまたはデータ範囲を選択します。  
  
3.  **ラベルの変更**ページ、ウィザードの 1 つの列が選択にドロップダウン リストから列を選択するか、列をクリックして、**データ サンプル**ウィンドウです。  
  
     **データ サンプル**ペインでは、約 50 行のデータにのみ示していますが、これらをサンプリングする値の適切な分散が表示されることを確認してください。  
  
     列のヘッダーをクリックして**カウント**各値のカウントで並べ替えを行う。  
  
     によって並べ替えることもできます**元のラベル**、再度すべての最大股は最小値を最初にラベルを付ける場合に便利です。  
  
4.  **ラベルの変更**データ ページ、ウィザードの 確認、**元のラベル**列で、グループ化または編集する方法を決定します。  
  
5.  下の行に新しい値を入力**新しいラベル**です。 値は、既存の値の一覧から選択できます。 新しい値は、入力した直後から再利用に使用できるようになります。  
  
6.  十分な行を入力したら、をクリックして**次**、し、、**先の選択**ページで、ラベルが変更されたデータの保存先を選択します。  
  
    -   **新しい列として、現在のワークシートに追加します。**  
  
         新しい値が格納されている列をテーブルに追加する場合に選択します。  
  
    -   **新しいワークシートに変更されたシートのデータをコピーします。**  
  
         更新されたデータが格納された新しいワークシートを作成する場合に選択します。  
  
    -   **データの場所を変更します。**  
  
         元データを新しい値に置き換える場合に選択します。  
  
## <a name="see-also"></a>参照  
 [データの探索とクリーニング](exploring-and-cleaning-data.md)  
  
  