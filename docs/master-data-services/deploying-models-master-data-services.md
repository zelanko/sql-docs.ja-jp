---
title: "モデル (Master Data Services) の展開 |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deployment packages [Master Data Services], about deployment packages
- deployment packages [Master Data Services]
ms.assetid: 30085c08-034f-4efe-80fe-408f9091ff5c
caps.latest.revision: 24
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 24067aaaceb2ad1e6704027c4445be9bf393a18f
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="deploying-models-master-data-services"></a>モデルの配置 (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]におけるパッケージは、配置可能なモデル構造と (必要に応じて) モデル データを含んだ XML ファイルです。 モデル パッケージを使用して、モデルのコピーを MDS 環境間で移動したり、既存の MDS 環境に新しいモデルを作成したりすることができます。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]**MDSModelDeploy ツール**で作成されたパッケージと旧バージョンとの互換性のある[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]またはそれ以降。  
  
## <a name="tools-for-deploying-models"></a>モデルを展開するためのツール  
 モデル パッケージを使用するには、3 つのツールをニーズに応じて使い分けることができます。  
  
-   **MDSModelDeploy ツール**: モデル オブジェクトとデータを作成して配置するには、MDSModelDeploy.exe ツールを使用します。 MDS のインストール時に既定のパスを選択した場合、 *drive*:\Program Files\Microsoft SQL Server\130\Master Data Services\Configuration にこのツールが格納されています。  
  
-   **モデル配置ウィザード**: モデルの構造のみのパッケージを作成して配置するには、 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web アプリケーションのウィザードを使用します。 このウィザードを使用して、データを配置することはできません。  
  
-   **モデル パッケージ エディター**: モデル パッケージを編集するには、ModelPackageEditor.exe を使用してモデル パッケージ エディター ウィザードを起動します。 このウィザードを使用して、MDSModelDeploy ツールまたはモデル配置ウィザードによって作成されたパッケージを編集します。 MDS のインストール時に既定のパスを選択した場合、 *drive*:\Program Files\Microsoft SQL Server\130\Master Data Services\Configuration にこのツールが格納されています。  
  
> [!IMPORTANT]  
>  MDSModelDeploy ツールを使用すると、新しいモデルの作成、モデルの複製の作成、または既存のモデルとそのデータの更新を実行できます。 MDSModelDeploy ツールを使用して既存のモデルとそのデータを更新するときに、配置先モデルに存在するエンティティ、属性、またはメンバーがパッケージに含まれていない場合は、MDSModelDeploy によって、そのエンティティ、属性、またはメンバーがモデルから削除されることはありません。  
  
## <a name="what-packages-contain"></a>パッケージに含められるもの  
 モデル パッケージは、.pkg 拡張子付きで保存される XML ファイルです。 配置パッケージを作成する場合、データを含めるかどうかを決定できます。 データを含める場合は、含めるデータのバージョンを選択する必要があります。  
  
 パッケージには、すべてのモデル オブジェクトが含まれています。 オブジェクトを次に示します。  
  
-   [エンティティ]  
  
-   属性  
  
-   属性グループ  
  
-   階層  
  
-   コレクション  
  
-   ビジネス ルール  
  
-   バージョン フラグ  
  
-   サブスクリプション ビュー  
  
 ファイル属性、ユーザーとグループのアクセス許可を含めることができません。 モデルを配置した後、これらを手動で更新する必要があります。  
  
## <a name="sample-packages"></a>サンプル パッケージ  
 サンプル パッケージ ファイルは [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]のインストールに含まれています。 このパッケージ ファイルは、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]をインストールした Master Data Services\Samples\Packages ディレクトリにあります。 MDSModelDeploy ツールを使用してサンプル パッケージを配置したときに、サンプル モデルが作成されデータが読み込まれます。  
  
## <a name="related-tasks"></a>関連タスク  
  
|タスクの説明|トピック|  
|----------------------|-----------|  
|MDSModelDeploy ツールを使用して、モデル オブジェクトとデータの新しい配置パッケージを作成します。|[MDSModelDeploy を使用して、モデルの配置パッケージを作成します。](../master-data-services/create-a-model-deployment-package-by-using-mdsmodeldeploy.md)|  
|ウィザードを使用して、モデル オブジェクトのみの新しい配置パッケージを作成します。|[ウィザードを使用してモデルの配置パッケージを作成します。](../master-data-services/create-a-model-deployment-package-by-using-the-wizard.md)|  
|MDSModelDeploy ツールを使用して、モデル オブジェクトとデータのパッケージを配置します。|[MDSModelDeploy を使用して、モデル配置パッケージを展開します。](../master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)|  
|ウィザードを使用して、モデル オブジェクトのみのパッケージを配置します。|[ウィザードを使用してモデル配置パッケージを展開します。](../master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md)|  
|モデル全体ではなく、モデルの選択した部分を配置するには、モデルの配置パッケージを編集します。|[モデルの配置パッケージを編集します。](../master-data-services/edit-a-model-deployment-package.md)|  
  
## <a name="related-content"></a>関連コンテンツ  
  
-   [モデル配置オプション & #40 です。マスター データ サービス &#41;](../master-data-services/model-deployment-options-master-data-services.md)  
  
  
