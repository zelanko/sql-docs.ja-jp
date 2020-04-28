---
title: ラベルの再付け (SQL Server データマイニングアドイン) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data preparation
- relabel
- data cleaning
ms.assetid: af041b39-fdd1-4cb5-a5ef-2f3ddab84614
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7f7d0accb835eb7da23ade6aec405066204fc415
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "78175601"
---
# <a name="relabel-sql-server-data-mining-add-ins"></a>ラベルの変更 (SQL Server データ マイニング アドイン)
  ![ラベルの変更ツールの Office 13 アイコン](media/dm13-relabel.gif "ラベルの変更ツールの Office 13 アイコン")

 Excel 用のデータ マイニング クライアントでは、データの新しいラベルを作成して、分析結果を理解しやすくできます。

 ラベルを変更する理由は次のとおりです。

-   データがコード化された結果を含んでいる場合 (たとえば 1 は男性、2 は女性など)。

-   バケット化した数値の範囲に、わかりやすい名前を付ける場合。

-   長い名前を簡単にする場合。

## <a name="using-the-relabel-wizard"></a>ラベルの変更ウィザードの使用

1.  [**データマイニング**] リボンで、[**クリーン**] をクリックし、[**再ラベル**] を選択します。

2.  Select the table or data range that has the data you want to fix.修正するデータが含まれているテーブルまたはデータ範囲を選択します。

3.  ウィザードの [**ラベル**の変更] ページで、ドロップダウンリストから列を選択するか、[**データサンプル**] ペインの列をクリックして、1つの列を選択します。

     [**データサンプル**] ペインには、約50行のデータのみが表示されますが、値が適切に分散されていることを確認するためにサンプリングされます。

     [**カウント**] の列ヘッダーをクリックすると、各値のカウント順に並べ替えられます。

     また、**元のラベル**で並べ替えることもできます。これは、最大値または最小値を最初に再ラベルする場合に便利です。

4.  ウィザードの [**ラベル**の変更] ページで、[**元のラベル**] 列の値を確認し、それらをグループ化または編集する方法を決定します。

5.  新しい**ラベル**の下の行に新しい値を入力します。 値は、既存の値の一覧から選択できます。 新しい値は、入力した直後から再利用に使用できるようになります。

6.  十分な行を入力したら、[**次へ**] をクリックし、[**変換先の選択**] ページで、再ラベル付けされたデータを保存する場所を選択します。

    -   **[現在のワークシートに新しい列として追加する]**

         新しい値が格納されている列をテーブルに追加する場合に選択します。

    -   **[変更されたシートのデータを新しいワークシートにコピーする]**

         更新されたデータが格納された新しいワークシートを作成する場合に選択します。

    -   **[配置データを変更する]**

         元データを新しい値に置き換える場合に選択します。

## <a name="see-also"></a>参照
 [データの探索とクリーニング](exploring-and-cleaning-data.md)


