---
title: '[増分更新] ダイアログボックス (Analysis Services-多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.process.incrementalupdate.f1
ms.assetid: d5a5ae27-44e7-4179-b9e2-efbf21d6c5f5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6115a5123fd6e72cee0ebccaac5f539be8aebfbe
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84544174"
---
# <a name="incremental-update-dialog-box-analysis-services---multidimensional-data"></a>[増分更新] ダイアログ ボックス (Analysis Services - 多次元データ)
  **および** の [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] [増分更新] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ダイアログ ボックスを使用すると、メジャー グループおよびパーティションの増分更新の際に使用される設定を定義できます。 **[増分更新]** ダイアログ ボックスを表示するには、 **[処理]** ダイアログ ボックスで **[オブジェクト一覧]** グリッドの **[設定]** 列にある **[構成]** をクリックします。  
  
## <a name="options"></a>オプション  
  
|期間|定義|  
|----------|----------------|  
|**メジャーグループ**|増分更新を行うメジャー グループを選択します。<br /><br /> 注: このオプションは、キューブの増分更新を行う場合にのみ有効です。 メジャー グループまたはパーティションの増分更新を行う場合、このオプションは無効です。|  
|**Partition**|更新するパーティションを選択します。<br /><br /> 注: このオプションは、キューブの増分更新を行う場合にのみ有効です。 メジャー グループまたはパーティションの増分更新を行う場合、このオプションは無効です。|  
|**テーブル**|テーブルにあるオブジェクトを更新します。|  
|**[データ ソースまたはビュー]**|ソース テーブルがあるデータ ソースまたはデータ ソース ビューを選択します。<br /><br /> 注: このオプションは、 **[テーブル]** が選択されている場合にのみ有効です。|  
|**[テーブルのスキーマと名前]**|キューブ、メジャー グループ、またはパーティションの増分更新を行うためのデータの取得に使用されるソース テーブルを選択します。<br /><br /> 注: このオプションは、 **[テーブル]** が選択されている場合にのみ有効です。|  
|**クエリ**|クエリにあるオブジェクトを更新します。|  
|**データ ソース**|クエリを実行するテーブルがあるデータ ソースを選択します。<br /><br /> 注: このオプションは、 **[クエリ]** が選択されている場合にのみ有効です。|  
|**[クエリ テキスト]**|キューブ、メジャー グループ、またはパーティションの増分更新を行うためのデータの取得に使用されるクエリのテキストを入力します。<br /><br /> 注: このオプションは、 **[クエリ]** が選択されている場合にのみ有効です。|  
  
## <a name="see-also"></a>参照  
 [多次元データ &#40;Analysis Services のデザイナーとダイアログボックス&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [[処理] ダイアログボックス &#40;Analysis Services-多次元データ&#41;](process-dialog-box-analysis-services-multidimensional-data.md)  
  
  
