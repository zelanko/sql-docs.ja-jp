---
title: "ビュー (Integration Services カタログ) |Microsoft ドキュメント"
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- views [Integration Services]
ms.assetid: d0294d43-4852-46dc-9afa-d0c19ea9aa03
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: b7293a70046df19eef816d3e7830518959ecbc98
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="views-integration-services-catalog"></a>ビュー (Integration Services カタログ)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  このセクションでは、[!INCLUDE[tsql](../../includes/tsql-md.md)] のインスタンスに配置されている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトを管理できる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ビューについて説明します。  
  
 クエリ、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]オブジェクト、設定、およびに格納されているオペレーション データを検査するビュー、 **SSISDB**カタログ。  
  
 カタログの既定の名前は、SSISDB です。 カタログに格納されているオブジェクトには、プロジェクト、パッケージ、パラメーター、環境、および操作履歴があります。  
  
 データベース ビューとストアド プロシージャを直接使用することも、マネージ API を呼び出すカスタム コードを記述することもできます。 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]マネージ API は、ビューに対してクエリし、多くのタスクを実行するには、このセクションで説明されているストアド プロシージャを呼び出します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [catalog.catalog_properties & #40 です。SSISDB データベース &#41;](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md)  
 プロパティを表示、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。  
  
 [catalog.effective_object_permissions & #40 です。SSISDB データベース &#41;](../../integration-services/system-views/catalog-effective-object-permissions-ssisdb-database.md)  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログのすべてのオブジェクトの現在のプリンシパルに対する有効な権限を表示します。  
  
 [catalog.environment_variables &#40;SSISDB データベース&#41;](../../integration-services/system-views/catalog-environment-variables-ssisdb-database.md)  
 すべての環境に対する環境変数の詳細を表示、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。  
  
 [catalog.environments &#40;SSISDB データベース&#41;](../../integration-services/system-views/catalog-environments-ssisdb-database.md)  
 すべての環境に対する環境の詳細を表示、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。 環境には、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトが参照できる変数が含まれています。  
  
 [catalog.execution_parameter_values &#40;SSISDB データベース&#41;](../../integration-services/system-views/catalog-execution-parameter-values-ssisdb-database.md)  
 インスタンスの実行中に [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージによって使用される実際のパラメーター値を表示します。  
  
 [catalog.executions &#40;SSISDB データベース&#41;](../../integration-services/system-views/catalog-executions-ssisdb-database.md)  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログのパッケージ実行のインスタンスを表示します。 パッケージ実行タスクで実行されるパッケージは、親パッケージと同じ実行のインスタンスで実行されます。  
  
 [catalog.explicit_object_permissions & #40 です。SSISDB データベース &#41;](../../integration-services/system-views/catalog-explicit-object-permissions-ssisdb-database.md)  
 ユーザーに明示的に割り当てられた権限のみを表示します。  
  
 [catalog.extended_operation_info &#40;SSISDB データベース&#41;](../../integration-services/system-views/catalog-extended-operation-info-ssisdb-database.md)  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログのすべての操作に対する拡張された情報を表示します。  
  
 [catalog.folders & #40 です。SSISDB データベース &#41;](../../integration-services/system-views/catalog-folders-ssisdb-database.md)  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログのフォルダーを表示します。  
  
 [catalog.object_parameters &#40;SSISDB データベース&#41;](../../integration-services/system-views/catalog-object-parameters-ssisdb-database.md)  
 すべてのパッケージのパラメーターを表示し、プロジェクトで、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。  
  
 [catalog.object_versions &#40;SSISDB データベース&#41;](../../integration-services/system-views/catalog-object-versions-ssisdb-database.md)  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログのオブジェクトのバージョンを示します。 このリリースでは、プロジェクトのバージョンのみがこのビューでサポートされます。  
  
 [catalog.operation_messages &#40;SSISDB データベース&#41;](../../integration-services/system-views/catalog-operation-messages-ssisdb-database.md)  
 操作中にログに記録されるメッセージが表示されます、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。  
  
 [catalog.operations &#40;SSISDB データベース&#41;](../../integration-services/system-views/catalog-operations-ssisdb-database.md)  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログのすべての操作の詳細を表示します。  
  
 [catalog.packages &#40;SSISDB データ&#41;](../../integration-services/system-views/catalog-packages-ssisdb-database.md)  
 表示されるすべてのパッケージの詳細を表示、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。  
  
 [catalog.environment_references &#40;SSISDB データベース&#41;](../../integration-services/system-views/catalog-environment-references-ssisdb-database.md)  
 すべてのプロジェクトに対する環境参照を表示、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。  
  
 [catalog.projects &#40;SSISDB データベース&#41;](../../integration-services/system-views/catalog-projects-ssisdb-database.md)  
 表示されるすべてのプロジェクトの詳細を表示、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。  
  
 [catalog.validations & #40 です。SSISDB データベース &#41;](../../integration-services/system-views/catalog-validations-ssisdb-database.md)  
 内のすべてのプロジェクトおよびパッケージ検証の詳細を表示、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。  
  
[catalog.master_properties & #40 です。SSISDB データベース &#41;](../../integration-services/system-views/catalog-master-properties-ssisdb-database.md)  
プロパティを表示、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]スケール アウト マスター。

[catalog.worker_agents & #40 です。SSISDB データベース &#41;](../../integration-services/system-views/catalog-worker-agents-ssisdb-database.md)  
情報が表示されます[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]スケール アウト ワーカーです。  

