---
title: "SQL Server の例: モデルの配置パッケージ (MDS) | Microsoft Docs"
ms.custom: 
ms.date: 07/28/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
keywords:
- "マスター データ サービス"
- sample
ms.assetid: 9b31b7b6-319b-4840-b67d-eb383e7762b1
caps.latest.revision: 21
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: bda0dbc730e24017dfc1978e691d3da654a15149
ms.contentlocale: ja-jp
ms.lasthandoff: 09/07/2017

---
# <a name="sql-server-examples-model-deployment-packages-mds"></a>SQL Server の例: モデルの配置パッケージ (MDS)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]をインストールすると、データの入ったサンプル モデル パッケージが追加されます。 サンプル モデル パッケージの既定の場所は、\<ドライブ>\Program Files\Microsoft SQL Server\130\Master Data Services\Samples\Packages です。  
  
 サンプル モデル パッケージを配置する方法については、「 [サンプル モデルとデータを配置する](../master-data-services/master-data-services-installation-and-configuration.md#deploySample)」を参照してください。 サンプル モデル パッケージは、 [MDSModelDeploy ツール](../master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)を使用して配置します。  
  
> [!IMPORTANT]  
>  **サンプルの更新: [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]**  
>   
>  次の新しい機能をサポートするためにサンプル パッケージが更新されました。  
>   
>  -   多対多リレーションシップの表示。  
>   
>      詳細については、「 [サンプル モデル内の M2M リレーションシップ](../master-data-services/show-many-to-many-relationships-in-derived-hierarchies-master-data-services.md#M2MSample)」を参照してください。  

> -   ドメイン ベースの属性の指定できる値を制限します。  
>   
>      詳細については、「[ドメイン ベースの属性を作成する (マスター データ サービス)](../master-data-services/create-a-domain-based-attribute-master-data-services.md)」を参照してください。  
> -   エンティティの変更に承認が必要。  
>   
>      詳細については、「[承認が必要 (マスター データ サービス)](../master-data-services/approval-required-master-data-services.md)」を参照してください。  
> -   ビジネス ルールでの Not および Else 演算子の使用。  
>   
>      詳細については、「 [ビジネス ルールの例](../master-data-services/business-rule-examples-master-data-services.md)」を参照してください。  
> -   カスタム インデックスの実装  
>   
>      詳細については、「[カスタム インデックス (マスター データ サービス)](../master-data-services/custom-index-master-data-services.md)」を参照してください。  
 

 
 マスター データ サービスのパッケージは、配置可能なモデル構造と (必要に応じて) モデル データを含んだ XML ファイルです。 モデル パッケージを使用して、モデルのコピーを MDS 環境間で移動したり、既存の [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 環境に新しいモデルを作成したりすることができます。  
  
## <a name="see-also"></a>参照  
 [MDSModelDeploy を使用したモデルの配置パッケージの配置](../master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)  
  
  

