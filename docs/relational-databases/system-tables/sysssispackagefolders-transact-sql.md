---
title: "sysssispackagefolders (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysdtspackagefolders90
- sysdtspackagefolders90_TSQL
dev_langs: TSQL
helpviewer_keywords: sysssispackagefolders system table
ms.assetid: ddc4833f-27bf-4610-b739-d257961d17ac
caps.latest.revision: "22"
author: spelluru
ms.author: spelluru
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: ec206dc0111235044ff7ea742548463db556ea23
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
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
  
  
