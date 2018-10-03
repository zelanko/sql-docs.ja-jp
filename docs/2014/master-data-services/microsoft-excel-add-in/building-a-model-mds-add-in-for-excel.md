---
title: モデルの構築 (Excel 用 MDS アドイン) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
ms.assetid: 8ae26ec3-c5d5-4c4f-a810-2951a7454439
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 297441a73dcf2ff6f6e0e1808f863c7641edfa30
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48190572"
---
# <a name="building-a-model-mds-add-in-for-excel"></a>モデルの構築 (Excel 用 MDS アドイン)
  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]の管理者は、 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションで利用可能な管理機能のサブセットを実行できます。  
  
 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] で管理者が実行できるモデル構築タスクは次のとおりです。  
  
-   エンティティを作成する。 エンティティの詳細については、「[エンティティ (マスター データ サービス)](../entities-master-data-services.md)」を参照してください。  
  
-   ドメイン ベースの属性を含む、すべての型の属性を作成する。 属性の詳細については、「[属性 (マスター データ サービス)](../attributes-master-data-services.md)」および「[ドメインベースの属性 (マスター データ サービス)](../domain-based-attributes-master-data-services.md)」を参照してください。  
  
 管理者は、 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションまたはWeb サービスを使用してモデルを作成する必要があります。 それにより、 [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] を使用してモデル内でエンティティや属性を作成できます。 モデル オブジェクトの詳細については、「[モデル (マスター データ サービス)](../models-master-data-services.md)」を参照してください。  
  
## <a name="related-tasks"></a>Related Tasks  
 ほとんどの管理タスクは、引き続き [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションまたは Web サービスを使用して実行する必要があります。 次の表に、管理者が MDS でタスクを完了するために使用できるツールを示します。  
  
|タスクの説明|ツール|トピック|  
|----------------------|----------|-----------|  
|モデルを作成する。|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションまたは Web サービス|[モデルを作成する&#40;マスター データ サービス&#41;](../create-a-model-master-data-services.md)|  
|エンティティを作成する。|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーション、Web サービス、または [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]|[エンティティの作成 &#40;Excel 用 MDS アドイン&#41;](create-an-entity-mds-add-in-for-excel.md)|  
|ドメイン ベースの属性を作成する。|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーション、Web サービス、または [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]|[ドメイン ベースの属性の作成 &#40;Excel 用 MDS アドイン&#41;](create-a-domain-based-attribute-mds-add-in-for-excel.md)|  
|属性グループを作成する。|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションまたは Web サービス|[属性グループを作成&#40;マスター データ サービス&#41;](../create-an-attribute-group-master-data-services.md)|  
|ビジネス ルールを作成する。|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションまたは Web サービス|[作成し、ビジネス ルールをパブリッシュ&#40;マスター データ サービス&#41;](../create-and-publish-a-business-rule-master-data-services.md)|  
|サブスクリプション ビューを作成する。|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションまたは Web サービス|[サブスクリプション ビューを作成&#40;マスター データ サービス&#41;](../create-a-subscription-view-to-export-data-master-data-services.md)|  
|階層を作成する。|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションまたは Web サービス|[派生階層を作成&#40;マスター データ サービス&#41;](../create-a-derived-hierarchy-master-data-services.md)<br /><br /> [明示的階層を作成&#40;マスター データ サービス&#41;](../create-an-explicit-hierarchy-master-data-services.md)|  
|コレクションを作成する。|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションまたは Web サービス|[コレクションを作成する&#40;マスター データ サービス&#41;](../create-a-collection-master-data-services.md)|  
|データのバージョンを作成する。|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションまたは Web サービス|[バージョンをロックする&#40;マスター データ サービス&#41;](../lock-a-version-master-data-services.md)|  
|モデルを配置する。|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーション、Web サービス、または MDSModelDeploy ツール|[MDSModelDeploy を使用したモデルの配置パッケージの作成](../create-a-model-deployment-package-by-using-mdsmodeldeploy.md)|  
  
## <a name="related-content"></a>関連コンテンツ  
  
-   [モデル (マスター データ サービス)](../models-master-data-services.md)  
  
-   [エンティティ (マスター データ サービス)](../entities-master-data-services.md)  
  
-   [属性&#40;マスター データ サービス&#41;](../attributes-master-data-services.md)  
  
-   [ドメイン ベース属性&#40;マスター データ サービス&#41;](../domain-based-attributes-master-data-services.md)  
  
-   [属性グループ&#40;マスター データ サービス&#41;](../attribute-groups-master-data-services.md)  
  
-   [ビジネス ルール (マスター データ サービス)](../business-rules-master-data-services.md)  
  
-   [データのエクスポート&#40;マスター データ サービス&#41;](../overview-exporting-data-master-data-services.md)  
  
-   [階層&#40;マスター データ サービス&#41;](../hierarchies-master-data-services.md)  
  
-   [コレクション&#40;マスター データ サービス&#41;](../collections-master-data-services.md)  
  
-   [バージョン&#40;マスター データ サービス&#41;](../versions-master-data-services.md)  
  
-   [セキュリティ &#40;マスター データ サービス&#41;](../security-master-data-services.md)  
  
-   [モデルの配置&#40;マスター データ サービス&#41;](../deploying-models-master-data-services.md)  
  
  
