---
title: 予測クエリの結果を表示して保存する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- prediction queries [Analysis Services]
- viewing prediction query results
- displaying prediction query results
- Mining Model Prediction [Analysis Services], viewing results
ms.assetid: abba4d24-3619-44c1-8279-88f27ad627d3
author: minewiskan
ms.author: owend
ms.openlocfilehash: f5fada79acb9a4dcac8ce3707ede13cfac96cc2f
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84520307"
---
# <a name="view-and-save-the-results-of-a-prediction-query"></a>予測クエリの結果の表示および保存
  で、予測クエリビルダーを使用してクエリを定義した後、クエリを実行して結果を表示するには、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] クエリ結果ビューに切り替えます。  
  
 予測クエリの結果は、プロジェクトで定義されている任意のデータソース内のテーブルに保存でき [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。 新しいテーブルを作成するか、または既存のテーブルにクエリ結果を保存できます。 既存のテーブルに結果を保存する場合は、テーブルに現在保存されているデータを上書きするように選択できます。上書きしない場合、クエリ結果は、テーブルの既存のデータに追加されます。  
  
### <a name="run-a-query-and-view-the-results"></a>クエリを実行し、結果を表示する  
  
1.  **のデータ マイニング デザイナーの** [マイニング モデル予測] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]タブにあるツール バーで、 **[結果]** をクリックします。  
  
     クエリ結果ビューが表示され、クエリが実行されます。 結果がビューアーのグリッドに表示されます。  
  
### <a name="save-the-results-of-a-prediction-query-to-a-table"></a>予測クエリの結果をテーブルに保存する  
  
1.  データ マイニング デザイナーの **[マイニング モデル予測]** タブのツール バーで、 **[クエリ結果の保存]** をクリックします。  
  
     **[データ マイニングのクエリ結果を保存]** ダイアログ ボックスが開きます。  
  
2.  **[データ ソース]** 一覧からデータ ソースを選択するか、 **[新規作成]** をクリックして新しいデータ ソースを作成します。  
  
3.  **[テーブル名]** ボックスにテーブルの名前を入力します。 同じテーブル名が既に存在する場合、テーブルの内容をクエリ結果に置き換えるには、 **[存在する場合は上書きする]** チェック ボックスをオンにします。 テーブルの内容を上書きしない場合は、このチェック ボックスをオフにします。 新しいクエリ結果が、テーブルの既存のデータに追加されます。  
  
4.  データ ソース ビューにテーブルを追加する場合は、 **[DSV に追加]** からデータ ソース ビューを選択します。  
  
5.  **[保存]** をクリックします。  
  
    > [!WARNING]  
    >  保存先で階層的な行セットがサポートされていない場合は、結果に FALTTENED キーワードを追加して、フラット テーブルとして保存できます。  
  
  
