---
title: sys.resource_usage (Azure SQL データベース) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- sys.resource_usage_TSQL
- resource_usage
- sys.resource_usage
- resource_usage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- resource_usage
- sys.resource_usage
ms.assetid: b90147a3-fd8e-408e-961d-5c7000e068ad
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 9b0e16279615bf102c916793439d440211939839
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63025419"
---
# <a name="sysresourceusage-azure-sql-database"></a>sys.resource_usage (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

    
> [!IMPORTANT]
>  この機能はプレビュー状態にします。 機能を変更または将来のリリースで削除された可能性がありますので、この機能の特定の実装に依存関係をなりません。  
> 
>  プレビュー状態で、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]運用チームには、この DMV のオンとオフのデータ収集が有効にすることがあります。  
> 
>  -   有効になっていると、DMV は集計時点の現在のデータを返します。  
> -   無効になっていると、DMV は古くなった可能性のある履歴データを返します。  
  
 現在のサーバーでユーザー データベースのリソース使用状況データの時間単位の概要を提供します。 履歴データは 90 日間保持されます。  
  
 各ユーザー データベースの 1 行が 1 時間ごとの継続的な方法で。 場合でも、データベースがアイドルであった時間内に、1 つの行があるし、そのデータベースの usage_in_seconds の値は 0 になります。 記憶域使用率と SKU については、ロール アップ時間の適切にします。  
  
|[列]|データ型|説明|  
|-------------|---------------|-----------------|  
|time|**datetime**|1 時間単位の時刻 (UTC)。|  
|database_name|**nvarchar**|ユーザー データベースの名前。|  
|sku|**nvarchar**|SKU の名前。 使用できる値を次に示します。<br /><br /> Web<br /><br /> ビジネス<br /><br /> Basic<br /><br /> Standard<br /><br /> Premium|  
|usage_in_seconds|**int**|1 時間の間隔において使用された CPU 時間の合計。<br /><br /> 注:この列は非推奨 v11 と V12 には適用されません。 **値は常に 0 に設定します。**|  
|storage_in_megabytes|**decimal**|データベースのデータ、インデックス、ストアド プロシージャ、およびメタデータを含む、1 時間の最大ストレージ サイズです。|  
  
## <a name="permissions"></a>アクセス許可  
 このビューは、仮想に接続するアクセス許可を持つすべてのユーザー ロールに使用可能な**マスター**データベース。  
  
  
