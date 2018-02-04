---
title: "sys.server_assembly_modules (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
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
- server_assembly_modules_TSQL
- sys.server_assembly_modules
- server_assembly_modules
- sys.server_assembly_modules_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_assembly_modules catalog view
ms.assetid: af799e38-2d16-49b2-bcf5-6f9199af899e
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ea4e4c55fbb2c8d153a841cb6d501b991b894241
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysserverassemblymodules-transact-sql"></a>sys.server_assembly_modules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  タイプ TA のサーバー レベル トリガーに対するアセンブリ モジュールごとに、1 行のデータを格納します。 このビューは、アセンブリ トリガーを、基になる CLR 実装にマップします。 この関係に参加できます**sys.server_triggers**です。 アセンブリに読み込まれている必要があります、**マスター**データベース。 この組 (object_id) はリレーションのキーになります。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|アセンブリ モジュールが定義されているオブジェクトへの FOREIGN KEY の逆参照。|  
|**assembly_id**|**int**|モジュールが作成された元のアセンブリの ID。 アセンブリは master データベースに読み込む必要があります。|  
|**assembly_class**|**sysname**|モジュールを定義しているアセンブリ内のクラスの名前。|  
|**assembly_method**|**sysname**|モジュールを定義しているクラス内のメソッドの名前。 集計関数 (AF) では NULL になります。|  
|**execute_as_principal_id**|**int**|EXECUTE AS サーバー プリンシパルの ID。<br /><br /> 既定値または EXECUTE AS CALLER の場合は、NULL になります。<br /><br /> 場合は、指定したプリンシパルの ID AS SELF EXECUTE AS の実行\<プリンシパル >。<br /><br /> -2 = EXECUTE AS OWNER。|  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [オブジェクト カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)  
  
  
