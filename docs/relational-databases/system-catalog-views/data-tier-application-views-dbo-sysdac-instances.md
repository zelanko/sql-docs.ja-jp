---
title: dbo.sysdac_instances (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dbo.sysdac_instances_TSQL
- sysdac_instances
- sysdac_instances_TSQL
- dbo.sysdac_instances
dev_langs:
- TSQL
helpviewer_keywords:
- dbo.sysdac_instances
- sysdac_instances
ms.assetid: 28285f3d-3889-439f-8b24-3bdef08e46b4
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1db50ced8cdff2f69b5dd3e8541b8c76e99cdae3
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="data-tier-application-views---dbosysdacinstances"></a>データ層アプリケーションのビュー - dbo.sysdac_instances
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに配置されたデータ層アプリケーション (DAC) インスタンスごとに 1 行を表示します。 sysdac_instances は、msdb データベースの dbo スキーマに属しています。 次の表では、sysdac_instances ビュー内の列について説明します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|instance_id|**uniqueidentifier**|DAC インスタンスの識別子。|  
|instance_name|**sysname**|DAC 配置時に指定された DAC インスタンスの名前。|  
|type_name|**sysname**|DAC パッケージの作成時に指定された DAC の名前。|  
|type_version|**nvarchar(64)**|DAC パッケージの作成時に指定された DAC のバージョン。|  
|description|**nvarchar (4000)**|DAC パッケージの作成時に指定された DAC の説明。|  
|type_stream|**varbinary(max)**|DAC に含まれる論理オブジェクト (テーブルやビューなど) のエンコード表現を含んでいるビット ストリーム。|  
|date_created|**datetime**|DAC インスタンスが作成された日時。|  
|created_by|**sysname**|DAC インスタンスを作成したログイン。|  
|database_name|**sysname**|DAC インスタンスのために作成したデータベースの名前。|  
  
## <a name="remarks"></a>解説  
 DAC には、アプリケーションが使用する論理データ層オブジェクト (テーブルやビューなど) の定義である DAC 型が含まれます。 DAC パッケージは、DAC の配置に使用されるファイルです。 DAC パッケージは、DAC 型に含まれるすべての論理オブジェクトの表現を含んでいます。 DAC パッケージは、1 つ以上のコピー、またはのインスタンスに dac のインスタンスを展開するために使用できます、[!INCLUDE[ssDE](../../includes/ssde-md.md)]です。 同じ DAC パッケージから配置された各 DAC インスタンスは、同じ型を共有しますが、一意のインスタンス名とインスタンス識別子を割り当てられます。  
  
## <a name="permissions"></a>権限  
 すべての列を表示するには、sysadmin 固定サーバー ロールのメンバーシップが必要です。 パブリック ロールのメンバーは、instance_name、description、および type_version の各列を表示できます。  
  
## <a name="see-also"></a>参照  
 [データ層アプリケーション](../../relational-databases/data-tier-applications/data-tier-applications.md)   
 [データ層アプリケーションのビュー &#40;です。TRANSACT-SQL と #41 です。](http://msdn.microsoft.com/library/0de01328-d7a6-4677-b7a0-dcd3098c23d4)  
  
  
