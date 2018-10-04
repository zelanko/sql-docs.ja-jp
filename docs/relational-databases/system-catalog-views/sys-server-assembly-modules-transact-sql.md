---
title: sys.server_assembly_modules (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a257f63328fe0abcf121b82b619bc58b70b7c6f7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47711706"
---
# <a name="sysserverassemblymodules-transact-sql"></a>sys.server_assembly_modules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  タイプ TA のサーバー レベル トリガーに対するアセンブリ モジュールごとに、1 行のデータを格納します。 このビューは、アセンブリ トリガーを、基になる CLR 実装にマップします。 このリレーションを結合する**sys.server_triggers**します。 アセンブリを読み込む必要がある、**マスター**データベース。 この組 (object_id) はリレーションのキーになります。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|アセンブリ モジュールが定義されているオブジェクトへの FOREIGN KEY の逆参照。|  
|**assembly_id**|**int**|モジュールが作成された元のアセンブリの ID。 アセンブリは master データベースに読み込む必要があります。|  
|**assembly_class**|**sysname**|モジュールを定義しているアセンブリ内のクラスの名前。|  
|**assembly_method**|**sysname**|モジュールを定義しているクラス内のメソッドの名前。 集計関数 (AF) では NULL になります。|  
|**execute_as_principal_id**|**int**|EXECUTE AS サーバー プリンシパルの ID。<br /><br /> 既定値または EXECUTE AS CALLER の場合は、NULL になります。<br /><br /> 指定したプリンシパルの ID AS SELF EXECUTE AS の実行\<プリンシパル >。<br /><br /> -2 = EXECUTE AS OWNER。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [オブジェクト カタログ ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)  
  
  
