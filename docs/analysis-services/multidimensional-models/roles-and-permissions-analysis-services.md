---
title: ロールと権限 (Analysis Services) |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5e6b463fedda33d8b10fbe2d1e415f1ef248ae92
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34025789"
---
# <a name="roles-and-permissions-analysis-services"></a>ロールと権限 (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]操作、オブジェクト、およびデータへのアクセスを付与するロール ベースの承認モデルを提供します。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスまたはデータベースにアクセスするすべてのユーザーは、ロールのコンテキスト内でアクセスする必要があります。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] システム管理者は、サーバーでの操作への無制限のアクセスが許可される **サーバー管理者ロール** へのメンバーシップの付与を担当します。 このロールの権限は固定されており、カスタマイズできません。 既定では、ローカルの Administrators グループのメンバーは、自動的に Analysis Services システム管理者になります。  
  
 データのクエリまたは処理を行う管理者以外のユーザーには、 **データベース ロール**によってアクセス権が付与されます。 システム管理者もデータベース管理者も、特定のデータベースでの異なるレベルのアクセスに対応するロールを作成し、アクセスを要するすべてのユーザーにメンバーシップを割り当てることができます。 各ロールには、特定のデータベース内のオブジェクトおよび操作にアクセスするための、カスタマイズされた一連の権限があります。 権限を割り当てられるレベルは、データベース、キューブやディメンションなどの内部オブジェクト (パースペクティブを除く)、および行です。  
  
 ロールの作成とメンバーシップの割り当ては、別の操作として行うのが一般的です。 多くの場合、モデル デザイナーは、デザイン フェーズ中にロールを追加します。 この方法で、すべてのロールの定義は、モデルを定義するプロジェクト ファイルに反映されます。 ロールのメンバーシップは、一般的には後でデータベースが実際に運用されるときに設定されます。通常は、データベース管理者が独立した操作として開発、テスト、および実行できるスクリプトを作成して設定します。  
  
 すべての承認は、有効な Windows ユーザー ID を前提としています。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、ユーザー ID の認証に Windows 認証だけを使用します。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]独自の認証メソッドを提供しません。参照してください[Analysis Services でサポートされる認証方法](../../analysis-services/instances/authentication-methodologies-supported-by-analysis-services.md)です。  
  
> [!IMPORTANT]  
>  権限は、データベース内のすべてのロールにわたって、Windows ユーザーまたはグループごとに加算的です。 1 つのロールで、あるユーザーまたはグループに対して特定のタスクの実行や、特定のデータの表示の権限を拒否しても、別のロールでこれらの権限がそのユーザーまたはグループに与えられる場合、ユーザーまたはグループはそのタスクの実行またはデータの表示の権限を持つことになります。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [オブジェクトと操作 & #40; への認証のアクセスAnalysis Services & #41;](../../analysis-services/multidimensional-models/authorizing-access-to-objects-and-operations-analysis-services.md)  
  
-   [データベースのアクセス許可を付与 & #40 です。Analysis Services & #41;](../../analysis-services/multidimensional-models/grant-database-permissions-analysis-services.md)  
  
-   [キューブまたはモデル権限 & #40; を許可します。Analysis Services & #41;](../../analysis-services/multidimensional-models/grant-cube-or-model-permissions-analysis-services.md)  
  
-   [処理権限の Grant & #40 です。Analysis Services & #41;](../../analysis-services/multidimensional-models/grant-process-permissions-analysis-services.md)  
  
-   [Grant 定義の読み取りアクセス許可オブジェクトのメタデータと #40 です。Analysis Services & #41;](../../analysis-services/multidimensional-models/grant-read-definition-permissions-on-object-metadata-analysis-services.md)  
  
-   [データ ソース オブジェクト & #40; に対する権限を付与します。Analysis Services & #41;](../../analysis-services/multidimensional-models/grant-permissions-on-a-data-source-object-analysis-services.md)  
  
-   [データ マイニング構造およびモデル & #40; に対する権限を付与します。Analysis Services & #41;](../../analysis-services/multidimensional-models/grant-permissions-on-data-mining-structures-and-models-analysis-services.md)  
  
-   [ディメンション & #40; に対する権限を付与します。Analysis Services & #41;](../../analysis-services/multidimensional-models/grant-permissions-on-a-dimension-analysis-services.md)  
  
-   [データ & #40; をディメンションにカスタムのアクセスを許可します。Analysis Services & #41;](../../analysis-services/multidimensional-models/grant-custom-access-to-dimension-data-analysis-services.md)  
  
-   [セル データへのカスタム アクセス権の付与 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-custom-access-to-cell-data-analysis-services.md)  
  
## <a name="see-also"></a>参照  
 [ロールの作成および管理](../../analysis-services/tabular-models/create-and-manage-roles-ssas-tabular.md)  
  
  
