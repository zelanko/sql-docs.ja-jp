---
title: '[リモートパーティション-詳細設定] ダイアログボックス (Analysis Services-多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.advancedrestoresettings.f1
ms.assetid: a03bb7e1-efaf-47c8-b0ee-f3e4438311cb
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1ca3f12ff53c4291d8bbe7c8eb97ce8e47172ea3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66070378"
---
# <a name="remote-partitions---advanced-settings-dialog-box-analysis-services---multidimensional-data"></a>[リモート パーティション - 詳細設定] ダイアログ ボックス (Analysis Services - 多次元データ)
  
  **で** [リモート パーティション - 詳細設定] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ダイアログ ボックスを使用すると、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] [データベースの復元] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ダイアログ ボックスでリモート バックアップ ファイルから **データベースへリモート パーティションを復元する際に、リモート パーティションを維持するリモート** データベースを表すデータ ソースの接続文字列などの詳細設定を編集できます。 
  **[リモート パーティション - 詳細設定]** ダイアログ ボックスを表示するには、 **[データベースの復元]** ダイアログ ボックスの **[パーティション]** ページで **[リモート パーティションを復元する]** オプションを選択した後、リモート パーティションの参照ボタン ( **[...]** ) をクリックします。  
  
## <a name="options"></a>オプション  
  
|期間|定義|  
|----------|----------------|  
|**データソース名**|一覧表示されたリモート パーティションを管理するリモート [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースを表すデータ ソースの名前を表示します。|  
|**バックアップファイル**|一覧表示されたリモート パーティションに対して復元されるデータを含むリモート バックアップ ファイルの名前を表示します。<br /><br /> 注: [**データベースの復元**] ダイアログボックスの [**パーティション**] ページの [**バックアップファイル**] 列でリモートバックアップファイルが指定されている場合、バックアップファイルは表示されません。|  
|**接続文字列**|
  **[データ ソース名]** に表示されているデータ ソースの接続文字列を表示します。|  
|**[編集]**|
  **データ リンク プロパティ** のダイアログ ボックスを表示し、接続文字列に含まれるプロパティを編集します。|  
|**パーティションの一覧**|リモート パーティションの復元先となる別の場所を指定します。 キューブ内のリモート パーティションに既定以外の場所を指定していた場合、リモート パーティションの復元フォルダーのみを変更できます。 各リモート パーティションに対して復元フォルダーを指定するには、このオプションが選択されている場合に有効となる次のグリッドを使用します。<br /><br /> **キューブ**: リモートパーティションを含むキューブの名前を表示します。<br /><br /> **MeasureGroup**: リモートパーティションを含むメジャーグループの名前を表示します。<br /><br /> **パーティション**: リモートパーティションの名前を表示します。<br /><br /> [**サイズ (MB)**]: リモートパーティションのサイズを mb 単位で表示します。<br /><br /> [**元のフォルダー**]: リモートパーティションが格納されていた元のフォルダーの名前が表示されます。<br /><br /> **復元フォルダー**: リモートパーティションの復元フォルダーの名前を入力するか、参照ボタン ([.**..**]) をクリックして [**リモートフォルダーの参照**] ダイアログボックスを表示し、使用するフォルダーのパスを選択します。 
  **[リモート フォルダーの参照]** ダイアログ ボックスの詳細については、「[[リモート フォルダーの参照] ダイアログ ボックス (Analysis Services - 多次元データ)](browse-for-remote-folder-dialog-box-analysis-services-multidimensional-data.md)」を参照してください。|  
  
## <a name="see-also"></a>参照  
 [多次元データ &#40;Analysis Services のデザイナーとダイアログボックス&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [パーティション &#40;[データベースの復元] ダイアログボックス&#41; &#40;Analysis Services-多次元データ&#41;](partitions-restore-database-dialog-box-analysis-services-multidimensional-data.md)   
 [Analysis Services データベースのバックアップと復元](multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  
