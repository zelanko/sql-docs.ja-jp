---
title: sys.filetable_system_defined_objects (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.filetable_system_defined_objects_TSQL
- filetable_system_defined_objects
- filetable_system_defined_objects_TSQL
- sys.filetable_system_defined_objects
dev_langs:
- TSQL
helpviewer_keywords:
- sys.filetable_system_defined_objects catalog view
ms.assetid: 62022e6b-46f6-495f-b14b-53f41e040361
caps.latest.revision: 9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 118646e7d12940291c0f4f6a79744495e596cf36
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43031094"
---
# <a name="sysfiletablesystemdefinedobjects-transact-sql"></a>sys.filetable_system_defined_objects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  FileTable に関連するシステム定義のオブジェクトの一覧が表示されます。 システム定義のオブジェクトごとに 1 行のデータを格納します。  
  
 FileTable を作成すると、関連するオブジェクト (制約、インデックスなど) が同時に作成されます。 これらのオブジェクトを変更または削除することはできません。これらは、FileTable 自体が削除されると一緒に削除されます。  
  
 FileTables について詳しくは、「[FileTables &#40;SQL Server&#41;](../../relational-databases/blob/filetables-sql-server.md)」をご覧ください。  
  
|[列]|データ型|説明|  
|------------|---------------|-----------------|  
|**object_id**|**int**|FileTable に関連するシステム定義オブジェクトのオブジェクト ID。<br /><br /> オブジェクト参照**sys.objects**します。|  
|**parent_object_id**|**int**|親 FileTable のオブジェクト ID。<br /><br /> オブジェクト参照**sys.objects**します。|  
  
## <a name="see-also"></a>参照  
 [FileTable の作成、変更、および削除](../../relational-databases/blob/create-alter-and-drop-filetables.md)   
 [FileTable の管理](../../relational-databases/blob/manage-filetables.md)  
  
  
