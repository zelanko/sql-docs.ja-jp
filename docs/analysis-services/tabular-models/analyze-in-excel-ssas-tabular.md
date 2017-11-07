---
title: "(SSAS テーブル) を Excel で分析 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2f17b4df-eea2-48c7-a1f2-a3fb7748c15f
caps.latest.revision: 19
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6450a75762b35816055efce444513c87e24eb3c4
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="analyze-in-excel"></a>[Excel で分析]
  Excel で分析機能、SSDT は、表形式モデルの作成者に迅速に開発中にモデル プロジェクトを分析する方法を提供します。 "Excel で分析" 機能によって Microsoft Excel が開き、モデル ワークスペース データベースへのデータ ソース接続が作成され、自動的にピボットテーブルがワークシートに追加されます。 ワークスペース データベース オブジェクト (テーブル、列、およびメジャー) は、ピボットテーブルのフィールドの一覧にフィールドとして含まれます。 これによりオブジェクトとデータは、有効なユーザーまたはロールおよびパースペクティブのコンテキスト内で表示できるようになります。  
  
 このトピックは、既に Microsoft Excel、ピボットテーブル、およびピボットグラフの使用に慣れているユーザーを対象としています。 Excel の使用方法の詳細については、Excel のヘルプを参照してください。  
  
##  <a name="bkmk_benefits"></a> 利点  
 "Excel で分析" 機能によって、モデルの作成者は Microsoft Excel という一般的なデータ分析アプリケーションを使用して、モデル プロジェクトの有効性をテストできます。 分析を Excel の機能を使用するのには、Microsoft Office 2003 必要があります。 または、後で SSDT と同じコンピューターにインストールされています。  
  
 "Excel で分析" 機能によって、Excel が開き、新しい Excel ブック (.xls) が作成されます。 ブックからモデル ワークスペース データベースへのデータ接続が作成されます。 空のピボットテーブルがワークシートに追加され、モデル オブジェクト メタデータがピボットテーブルのフィールドの一覧に入力されます。 これで、表示可能なデータとスライサーをピボットテーブルに追加できます。  
  
 "Excel で分析" 機能を使用する際に、既定では、現在ログオンしているユーザー アカウントが有効なユーザーになります。 このアカウントは通常、モデル オブジェクトまたはデータに対する表示制限のない管理者です。 ただし、別の有効なユーザー名またはロールを指定することもできます。 これにより、特定のユーザーまたはロールのコンテキスト内で Excel のモデル プロジェクトを参照できます。 有効なユーザーの指定には、次のオプションが含まれています。  
  
 **[現在の Windows ユーザー]**  
 現在ログオンしているユーザー アカウントを使用します。  
  
 **[その他の Windows ユーザー]**  
 現在ログオンしているユーザーではなく、指定した Windows ユーザー名を使用します。 別の Windows ユーザーを使用する場合、パスワードは必要ありません。 有効なユーザー名のコンテキスト内で Excel を使用して、オブジェクトおよびデータを表示することのみが可能になります。 Excel でモデル オブジェクトまたはデータに変更を行うことはできません。  
  
 **ロール**  
 ロールは、オブジェクト メタデータおよびデータに対するユーザーの権限の定義に使用されます。 ロールは通常、特定の Windows ユーザーまたは Windows ユーザー グループに対して定義されます。 一部の適切なロールには、DAX 式で定義した追加の行レベル フィルターを含めることができます。 "Excel で分析" 機能を使用する際には、必要に応じて使用するロールを選択することもできます。 オブジェクト メタデータおよびデータの表示は、ロールに対して定義された権限とフィルターによって制限されます。 詳細については、次を参照してください。[作成と管理の役割](../../analysis-services/tabular-models/create-and-manage-roles-ssas-tabular.md)です。  
  
 有効なユーザーまたはロールに加え、パースペクティブを指定することもできます。 モデル作成者はパースペクティブを使用して、ビジネス シナリオに基づいてモデル オブジェクトとデータの表示を定義できます。 既定では、パースペクティブは使用されません。 でパースペクティブを Excel で分析を使用するためにパースペクティブが既に SSDT では、[パースペクティブ] ダイアログ ボックスを使用して定義する必要があります。 パースペクティブが指定されている場合、ピボットテーブルのフィールドの一覧には、パースペクティブで選択されたオブジェクトのみが表示されます。 詳細については、次を参照してください。[管理パースペクティブの作成および](../../analysis-services/tabular-models/create-and-manage-perspectives-ssas-tabular.md)です。  
  
##  <a name="bkmk_rt"></a> Related tasks  
  
|**トピック**|**Description**|  
|---------------|---------------------|  
|[Excel でテーブル モデルを分析します。](../../analysis-services/tabular-models/analyze-a-tabular-model-in-excel-ssas-tabular.md)|このトピックでは、モデル デザイナーで "Excel で分析" 機能を使用する方法、モデル ワークスペース データベースへのデータ ソース接続を作成する方法、およびワークシートにピボットテーブルを追加する方法について説明します。|  
  
## <a name="see-also"></a>参照  
 [Excel でテーブル モデルを分析します。](../../analysis-services/tabular-models/analyze-a-tabular-model-in-excel-ssas-tabular.md)   
 [ロール](../../analysis-services/tabular-models/roles-ssas-tabular.md)   
 [パースペクティブ](../../analysis-services/tabular-models/perspectives-ssas-tabular.md)  
  
  

