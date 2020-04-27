---
title: '[データベースのプロパティ] ダイアログボックス (SSAS-多次元) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.databaseproperties.f1
ms.assetid: 70f000b7-917f-4699-b142-7a0d13ff767c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: be4133aa143ecf0e1fb9b50c40a38a73b4207f30
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66082318"
---
# <a name="database-properties-dialog-box-ssas---multidimensional"></a>[データベースのプロパティ] ダイアログ ボックス (SSAS - 多次元)
  **の** [データベースのプロパティ] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ダイアログ ボックスを使用すると、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースのプロパティを設定できます。 **[データベースのプロパティ]** ダイアログ ボックスを表示するには、オブジェクト エクスプローラーでデータベースを右クリックし、 **[プロパティ]** を選択します。  
  
## <a name="options"></a>オプション  
  
|用語|定義|  
|----------|----------------|  
|**名前**|データベースの名前を変更するときに、名前を入力します。|  
|**ID**|データベースの ID が表示されます。|  
|**説明**|データベースの説明を変更するときに、説明を入力します。|  
|**[タイムスタンプの作成]**|データベースが作成された日時が表示されます。|  
|**[スキーマの最終更新]**|データベースのメタデータが最後に更新されたときの日時が表示されます。|  
|**[最終更新]**|データベースのデータが最後に更新されたときの日時が表示されます。|  
|**[データ ソースの権限借用情報]**|データベースに含まれているデータ ソースに接続したり操作したりするときに、データベースで使用される権限借用情報を選択します。 有効な値は次のとおりです。<br /><br /> **ImpersonateAccount** (特定の Windows ユーザー名とパスワードを使用します)。<br /><br /> **ImpersonateService** (サービス アカウントを使用します)。<br /><br /> **ImpersonateCurrentUser** (現在のユーザーの資格情報を使用します)。<br /><br /> **Default** (MOLAP 操作にはサービス アカウントを使用し、データ マイニングには現在のユーザーを使用します)。<br /><br /> データベース レベルでデータ ソースの権限借用の設定を行えますが、そのように設定すると、権限借用の設定に対して **[継承]** を指定しているデータ ソースだけが影響を受けます。 データ ソースで直接指定された権限借用の設定は、常に、データベース レベルで指定されている設定をオーバーライドします。<br /><br /> 権限借用のオプションを選択するときは、サポートされる必要のある操作の種類を考慮してください。 処理などの一部の操作は実行できません。|  
|**[最終処理]**|データベースが最後に処理された日時が表示されます。|  
|**[推定サイズ]**|データベースの推定サイズが表示されます。|  
|**ストレージの場所**|データベースの場所を指定します。 データベースが既定のデータ ディレクトリにある場合は、この値は空になります。|  
  
## <a name="see-also"></a>参照  
 [多次元データ &#40;Analysis Services のデザイナーとダイアログボックス&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [多次元モデル データベース &#40;SSAS&#41;](multidimensional-models/multidimensional-model-databases-ssas.md)  
  
  
