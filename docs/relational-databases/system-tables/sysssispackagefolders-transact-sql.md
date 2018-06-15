---
title: sysssispackagefolders (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysdtspackagefolders90
- sysdtspackagefolders90_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysssispackagefolders system table
ms.assetid: ddc4833f-27bf-4610-b739-d257961d17ac
caps.latest.revision: 22
author: douglasl
ms.author: douglasl
manager: craigg
ms.openlocfilehash: fb24e752bf92704b1560aa84906f28173a0d9dc0
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33258253"
---
# <a name="sysssispackagefolders-transact-sql"></a>sysssispackagefolders (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  フォルダー階層内の論理フォルダーごとに 1 行が含まれていますを[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]を使用します。 オブジェクト エクスプ ローラーでのこれらのフォルダーが表示されている[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]への接続時[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]です。 フォルダーには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] またはファイル システムに保存されているパッケージが一覧表示されます。  
  
 **Parentfolderid**列には、フォルダー階層がについて説明します。 フォルダー階層の最上位にあるフォルダーには内で null 値が含まれています**parentfolderid**です。  
  
 **Foldername**列には、オブジェクト エクスプ ローラーで表示されるフォルダーの名前が含まれています。  
  
 次の表は、 **msdb**データベース。  

  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**folderid**|**uniqueidentifier**|フォルダーの GUID。|  
|**parentfolderid**|**uniqueidentifier**|親フォルダーの GUID。|  
|**フォルダー名**|**sysname**|フォルダーの名前。 これは、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] でフォルダー階層に表示される名前です。|  
  
  
