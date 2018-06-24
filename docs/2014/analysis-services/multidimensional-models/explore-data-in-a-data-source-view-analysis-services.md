---
title: データ ソース ビュー (Analysis Services) でデータを探索 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- exploring data [Analysis Services]
- data source views [Analysis Services], exploring data
- viewing source data
ms.assetid: 2c922c35-fbcb-45b2-96b1-c7a846d8b419
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: e4fcb284eeb85b820ce0a194787337fa51e9e345
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36075618"
---
# <a name="explore-data-in-a-data-source-view-analysis-services"></a>データ ソース ビューでのデータの検索 (Analysis Services)
  **のデータ ソース ビュー デザイナーにある** [データの探索] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ダイアログ ボックスを使用すると、テーブル、ビュー、または名前付きクエリのデータをデータ ソース ビュー (DSV) で参照できます。 データ ソース ビュー デザイナーでデータを探索すると、選択したテーブル、ビュー、または名前付きクエリの各データ列の内容を表示できます。 実際の内容を表示すると、すべての列が必要であるかどうか、使いやすさを向上させるために名前付き計算が必要であるかどうか、既存の名前付き計算または名前付きクエリによって予想値が返されるかどうかなどを判断できます。  
  
 データを表示するには、DSV で選択したオブジェクトのデータ ソースに対するアクティブな接続が必要です。 また、テーブル内の名前付き計算もクエリで送信されます。  
  
 データは表形式で返されるので、並べ替えてコピーできます。 列のヘッダーをクリックすると、その列で行が再度並べ替えられます。 グリッドでデータを選択して、Ctrl キーを押しながら C キーを押すと、選択範囲をクリップボードにコピーできます。  
  
 また、サンプリング方法やサンプル数を制御することもできます。 既定では、上位 5,000 行が返されます。  
  
## <a name="to-browse-data-or-change-sampling-options"></a>データの参照またはサンプリング オプションを変更するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]でプロジェクトを開くか、またはデータを参照するデータ ソース ビューが含まれているデータベースに接続します。  
  
2.  ソリューション エクスプローラーで、 **[データ ソース ビュー]** フォルダーを展開して、データ ソース ビューをダブルクリックします。  
  
3.  表示するデータが含まれているテーブル、ビュー、または名前付きクエリを右クリックして、 **[データの探索]** をクリックします。  
  
     データ ソースの基になるテーブル、ビュー、または名前付きクエリ、データ ソース ビューのクエリ、および、結果に表示されます、**探索\<オブジェクト名 > テーブル**タブです。  
  
4.  **エクスプ ローラー\<オブジェクト名 > テーブル**ツールバーで、をクリックして、**サンプリング オプション**アイコン。  
  
     **[データ探索オプション]** ダイアログ ボックスが開きます。 このダイアログ ボックスでは、サンプリング方法 (既定のサンプリング サイズである 5,000 行以外のレコード数) またはサンプル数を指定できます。  
  
5.  **[OK]** または **[キャンセル]** をクリックします。  
  
6.  データをリサンプルして**サンプル データの**上、**エクスプ ローラー\<オブジェクト名 > テーブル**ツールバー。  
  
## <a name="see-also"></a>参照  
 [多次元モデルのデータ ソース ビュー](data-source-views-in-multidimensional-models.md)  
  
  