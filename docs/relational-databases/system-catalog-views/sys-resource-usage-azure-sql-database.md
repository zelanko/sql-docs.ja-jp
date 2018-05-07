---
title: sys.resource_usage (Azure SQL データベース) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/03/2017
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: system-catalog-views
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
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
caps.latest.revision: 15
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: cc8f9c68bd6074439203c384c99b407022f90997
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sysresourceusage-azure-sql-database"></a>sys.resource_usage (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

    
> [!IMPORTANT]  
>  この機能は現在プレビュー状態です。 この機能は将来のリリースで変更または削除される可能性があるので、この機能の特定の実装に依存する設定は行わないでください。  
>   
>  プレビュー状態のときに、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]運用チームには、この DMV のオンとオフのデータ収集が有効にすることがあります。  
>   
>  -   有効になっていると、DMV は集計時点の現在のデータを返します。  
> -   無効になっていると、DMV は古くなった可能性のある履歴データを返します。  
  
 現在のサーバーにあるユーザー データベースのリソースの使用状況に関するデータの概要を 1 時間単位で表示します。 履歴データには、90 日間は保持されます。  
  
 ユーザー データベース別に、1 時間分のデータが 1 行ずつ連続して表示されます。 データベースが 1 時間アイドル状態であっても、それに対応する 1 行は表示され、そのデータベースの usage_in_seconds の値は 0 になります。 ストレージの使用状況と SKU に関する情報は、それに応じて 1 時間分ロール アップされます。  
  
|列|データ型|Description|  
|-------------|---------------|-----------------|  
|time|**datetime**|1 時間単位の時刻 (UTC)。|  
|database_name|**nvarchar**|ユーザー データベースの名前です。|  
|sku|**nvarchar**|SKU の名前です。 使用できる値を次に示します。<br /><br /> Web<br /><br /> ビジネス<br /><br /> 基本<br /><br /> Standard<br /><br /> Premium|  
|usage_in_seconds|**int**|1 時間の間隔において使用された CPU 時間の合計。<br /><br /> 注: この列は v11 非推奨であり、V12 には適用されません。 **値は常に、0 に設定します。**|  
|storage_in_megabytes|**decimal**|1 時間の間隔の最大ストレージ サイズ。これにはデータベースのデータ、インデックス、ストアド プロシージャ、メタデータが含まれます。|  
  
## <a name="permissions"></a>権限  
 このビューは、仮想に接続する権限を持つすべてのユーザー ロールに利用可能な**マスター**データベース。  
  
  
