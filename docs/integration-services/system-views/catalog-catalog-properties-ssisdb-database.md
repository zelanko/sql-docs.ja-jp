---
title: "catalog.catalog_properties (SSISDB データベース) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: e604a382-95c8-4764-b268-742eb5c6d4cf
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: ca3d5da05126d5b71bf6d714f9e8449f9f5c8335
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="catalogcatalogproperties-ssisdb-database"></a>catalog.catalog_properties (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  プロパティを表示、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|property_name|**nvarchar (256)**|カタログ プロパティの名前。|  
|property_value|**nvarchar (256)**|カタログ プロパティの値。|  
  
## <a name="remarks"></a>解説  
 このビューは、各カタログ プロパティの行を表示します。 このビューで表示されるプロパティは、次のとおりです。  
  
|プロパティ名|Description|  
|-------------------|-----------------|  
|**ENCRYPTION_ALGORITHM**|機密データの暗号化に使用される暗号化アルゴリズムの種類。 サポートされている値が含まれます: `DES`、 `TRIPLE_DES`、 `TRIPLE_DES_3KEY`、 `DESX`、 `AES_128`、 `AES_192`、および`AES_256`です。 注: プロパティを変更するには、カタログ データベースがシングル ユーザー モードである必要があります。|  
|**MAX_PROJECT_VERSIONS**|1 つのプロジェクトで保持される新しいプロジェクト バージョンの数。 バージョンのクリーンアップを有効にすると、この数を超える以前のバージョンは削除されます。|  
|**OPERATION_CLEANUP_ENABLED**|値が`TRUE`、操作の詳細と操作のメッセージよりも古い**RETENTION_WINDOW** (日) は、カタログから削除されます。 値が `FALSE` の場合は、すべての操作の詳細と操作のメッセージがカタログに格納されます。 注:[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ジョブ操作のクリーンアップで実行されます。|  
|**RETENTION_WINDOW**|操作の詳細と操作のメッセージがカタログに格納される日数。 値が`-1`、保有ウィンドウは無期限です。 注: クリーンアップが必要ない場合は設定**OPERATION_CLEANUP_ENABLED**に**FALSE**です。|  
|**VALIDATION_TIMEOUT**|検証が、このプロパティで指定された秒数で完了しなかった場合、検証は停止します。|  
|**VERSION_CLEANUP_ENABLED**|値が`TRUE`、のみ、 **MAX_PROJECT_VERSIONS**プロジェクト バージョンの数は、カタログに格納され、他のすべてのプロジェクトのバージョンが削除されます。 値が**FALSE**、すべてのプロジェクト バージョンがカタログに格納されます。 注:[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ジョブ操作のクリーンアップで実行されます。|  
|**SERVER_LOGGING_LEVEL**|既定のログ記録レベル、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]サーバー。|  
  
## <a name="permissions"></a>Permissions  
 このビューには、次の権限のいずれかが必要です。  
  
-   メンバーシップを**ssis_admin**データベース ロール  
  
-   メンバーシップを**sysadmin**サーバーの役割  
  
  
