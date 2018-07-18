---
title: '[増分更新] ダイアログ ボックス (Analysis Services - 多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.process.incrementalupdate.f1
ms.assetid: d5a5ae27-44e7-4179-b9e2-efbf21d6c5f5
caps.latest.revision: 19
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 22d7038fa3d8f07c5b32e35c5cb39e0d8db95766
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37284168"
---
# <a name="incremental-update-dialog-box-analysis-services---multidimensional-data"></a>[増分更新] ダイアログ ボックス (Analysis Services - 多次元データ)
  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] および [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] の **[増分更新]** ダイアログ ボックスを使用すると、メジャー グループおよびパーティションの増分更新の際に使用される設定を定義できます。 **[増分更新]** ダイアログ ボックスを表示するには、 **[処理]** ダイアログ ボックスで **[オブジェクト一覧]** グリッドの **[設定]** 列にある **[構成]** をクリックします。  
  
## <a name="options"></a>および  
  
|項目|定義|  
|----------|----------------|  
|**[メジャー グループ]**|増分更新を行うメジャー グループを選択します。<br /><br /> 注: このオプションは、キューブの増分更新を行う場合にのみ有効です。 メジャー グループまたはパーティションの増分更新を行う場合、このオプションは無効です。|  
|**パーティション**|更新するパーティションを選択します。<br /><br /> 注: このオプションは、キューブの増分更新を行う場合にのみ有効です。 メジャー グループまたはパーティションの増分更新を行う場合、このオプションは無効です。|  
|**Table**|テーブルにあるオブジェクトを更新します。|  
|**データ ソースまたはビュー**|ソース テーブルがあるデータ ソースまたはデータ ソース ビューを選択します。<br /><br /> 注: このオプションは、 **[テーブル]** が選択されている場合にのみ有効です。|  
|**テーブルのスキーマと名前**|キューブ、メジャー グループ、またはパーティションの増分更新を行うためのデータの取得に使用されるソース テーブルを選択します。<br /><br /> 注: このオプションは、 **[テーブル]** が選択されている場合にのみ有効です。|  
|**クエリ**|クエリにあるオブジェクトを更新します。|  
|**Data Source**|クエリを実行するテーブルがあるデータ ソースを選択します。<br /><br /> 注: このオプションは、 **[クエリ]** が選択されている場合にのみ有効です。|  
|**クエリのテキスト**|キューブ、メジャー グループ、またはパーティションの増分更新を行うためのデータの取得に使用されるクエリのテキストを入力します。<br /><br /> 注: このオプションは、 **[クエリ]** が選択されている場合にのみ有効です。|  
  
## <a name="see-also"></a>参照  
 [Analysis Services のデザイナーおよびダイアログ ボックス&#40;多次元データ&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [[プロセス] ダイアログ ボックス&#40;Analysis Services - 多次元データ&#41;](process-dialog-box-analysis-services-multidimensional-data.md)  
  
  
