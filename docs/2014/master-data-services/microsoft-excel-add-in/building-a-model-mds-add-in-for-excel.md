---
title: モデルの構築 (Excel 用 MDS アドイン) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 8ae26ec3-c5d5-4c4f-a810-2951a7454439
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: ee3473ba16ad3a03a95065aea94888654db53187
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "65479346"
---
# <a name="building-a-model-mds-add-in-for-excel"></a>モデルの構築 (Excel 用 MDS アドイン)
  
  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]
  [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]の管理者は、 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションで利用可能な管理機能のサブセットを実行できます。  
  
 
  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]
  [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] で管理者が実行できるモデル構築タスクは次のとおりです。  
  
-   エンティティを作成する。 エンティティの詳細については、「 [エンティティ (マスター データ サービス)](../entities-master-data-services.md)」を参照してください。  
  
-   ドメイン ベースの属性を含む、すべての型の属性を作成する。 属性の詳細については、「 [属性 (マスター データ サービス)](../attributes-master-data-services.md) 」および「 [ドメインベースの属性 (マスター データ サービス)](../domain-based-attributes-master-data-services.md)」を参照してください。  
  
 管理者は、 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションまたはWeb サービスを使用してモデルを作成する必要があります。 それにより、 [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] を使用してモデル内でエンティティや属性を作成できます。 モデル オブジェクトの詳細については、「 [モデル (マスター データ サービス)](../models-master-data-services.md)」を参照してください。  
  
## <a name="related-tasks"></a>Related Tasks  
 ほとんどの管理タスクは、引き続き [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションまたは Web サービスを使用して実行する必要があります。 次の表に、管理者が MDS でタスクを完了するために使用できるツールを示します。  
  
|タスクの説明|ツール|トピック|  
|----------------------|----------|-----------|  
|モデルを作成する。|
  [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションまたは Web サービス|[モデル &#40;マスターデータサービスを作成し&#41;](../create-a-model-master-data-services.md)|  
|エンティティを作成する。|
  [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーション、Web サービス、または [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]|[エンティティ &#40;Excel 用 MDS アドインを作成し&#41;](create-an-entity-mds-add-in-for-excel.md)|  
|ドメイン ベースの属性を作成する。|
  [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーション、Web サービス、または [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]|[ドメインベースの属性 &#40;Excel 用 MDS アドインを作成&#41;](create-a-domain-based-attribute-mds-add-in-for-excel.md)|  
|属性グループを作成する。|
  [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションまたは Web サービス|[属性グループ &#40;マスターデータサービスを作成し&#41;](../create-an-attribute-group-master-data-services.md)|  
|ビジネス ルールを作成する。|
  [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションまたは Web サービス|[ビジネスルール &#40;マスターデータサービスを作成して発行&#41;](../create-and-publish-a-business-rule-master-data-services.md)|  
|サブスクリプション ビューを作成する。|
  [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションまたは Web サービス|[サブスクリプションビュー &#40;マスターデータサービスを作成し&#41;](../create-a-subscription-view-to-export-data-master-data-services.md)|  
|階層を作成する。|
  [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションまたは Web サービス|[派生階層 &#40;マスターデータサービスを作成し&#41;](../create-a-derived-hierarchy-master-data-services.md)<br /><br /> [明示的階層 &#40;マスターデータサービスを作成し&#41;](../create-an-explicit-hierarchy-master-data-services.md)|  
|コレクションを作成する。|
  [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションまたは Web サービス|[コレクション &#40;マスターデータサービスを作成し&#41;](../create-a-collection-master-data-services.md)|  
|データのバージョンを作成する。|
  [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションまたは Web サービス|[マスターデータサービス &#40;のバージョンをロックする&#41;](../lock-a-version-master-data-services.md)|  
|モデルを配置する。|
  [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーション、Web サービス、または MDSModelDeploy ツール|[MDSModelDeploy を使用したモデルの配置パッケージの作成](../create-a-model-deployment-package-by-using-mdsmodeldeploy.md)|  
  
## <a name="related-content"></a>関連コンテンツ  
  
-   [モデル &#40;マスターデータサービス&#41;](../models-master-data-services.md)  
  
-   [エンティティ &#40;マスターデータサービス&#41;](../entities-master-data-services.md)  
  
-   [属性 &#40;マスターデータサービス&#41;](../attributes-master-data-services.md)  
  
-   [ドメインベースの属性 &#40;マスターデータサービス&#41;](../domain-based-attributes-master-data-services.md)  
  
-   [属性グループ &#40;マスターデータサービス&#41;](../attribute-groups-master-data-services.md)  
  
-   [ビジネスルール &#40;マスターデータサービス&#41;](../business-rules-master-data-services.md)  
  
-   [データのエクスポート &#40;マスターデータサービス&#41;](../overview-exporting-data-master-data-services.md)  
  
-   [階層 &#40;マスターデータサービス&#41;](../hierarchies-master-data-services.md)  
  
-   [コレクション &#40;マスターデータサービス&#41;](../collections-master-data-services.md)  
  
-   [バージョン &#40;マスターデータサービス&#41;](../versions-master-data-services.md)  
  
-   [セキュリティ &#40;マスターデータサービス&#41;](../security-master-data-services.md)  
  
-   [モデルの配置 &#40;マスターデータサービス&#41;](../deploying-models-master-data-services.md)  
  
  
