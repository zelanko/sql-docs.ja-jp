---
title: "catalog.projects (SSISDB データベース) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: a6b595e1-5227-47ce-8ee2-a28c1e1d5645
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 668890ae464deb8dfa029eab38b608fee12af0ca
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="catalogprojects-ssisdb-database"></a>catalog.projects (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  表示されるすべてのプロジェクトの詳細を表示、 **SSISDB**カタログ。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|project_id|**bigint**|プロジェクトの一意識別子 (ID)。|  
|folder_id|**bigint**|プロジェクトがあるフォルダーの一意の ID。|  
|name|**sysname**|プロジェクトの名前。|  
|description|**nvarchar (1024)**|プロジェクトの説明 (省略可)。|  
|project_format_version|**int**|バージョン[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]プロジェクトの開発に使用されました。|  
|deployed_by_sid|**varbinary (85)**|プロジェクトをインストールしたユーザーのセキュリティ識別子 (SID)。|  
|deployed_by_name|**nvarchar (128)**|プロジェクトをインストールしたユーザーの名前。|  
|last_deployed_time|**datetimeoffset (7)**|パッケージを配置または再配置した日付と時刻。|  
|created_time|**datetimeoffset (7)**|プロジェクトが作成された日時。|  
|object_version_lsn|**bigint**|プロジェクトのバージョン。 この番号は、シーケンシャルを保証するものではありません。|  
|validation_status|**char (1)**|検証状態。|  
|last_validation_time|**datetimeoffset (7)**|前回の検証操作の時刻。|  
  
## <a name="remarks"></a>解説  
 このビューは、カタログの各プロジェクトの行を表示します。  
  
## <a name="permissions"></a>Permissions  
 このビューには、次の権限のいずれかが必要です。  
  
-   プロジェクトに対する READ 権限  
  
-   メンバーシップを**ssis_admin**データベース ロール  
  
-   メンバーシップを**sysadmin**サーバーの役割です。  
  
> [!NOTE]  
>  プロジェクトの READ 権限がある場合は、そのプロジェクトに関連付けられたすべてのパッケージおよび環境の READ 権限もあります。 行レベルのセキュリティが適用されるため、表示する権限がある行のみが表示されます。  
  
  
