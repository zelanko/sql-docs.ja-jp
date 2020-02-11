---
title: sysssispackagefolders (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdtspackagefolders90
- sysdtspackagefolders90_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysssispackagefolders system table
ms.assetid: ddc4833f-27bf-4610-b739-d257961d17ac
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d2ff4537f5db246dd9bcdc114b02005402f8745f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68029592"
---
# <a name="sysssispackagefolders-transact-sql"></a>sysssispackagefolders (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  が使用する[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]フォルダー階層内の論理フォルダーごとに1行のレコードを格納します。 これらのフォルダーは、に[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]接続するときにオブジェクトエクスプローラーの一覧に表示されます。 フォルダーには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] またはファイル システムに保存されているパッケージが一覧表示されます。  
  
 **Parentfolderid**列には、フォルダー階層が記述されています。 フォルダー階層の最上位にあるフォルダーには、 **parentfolderid**に null 値が含まれています。  
  
 **Foldername**列にはオブジェクトエクスプローラーに表示されるフォルダーの名前が含まれています。  
  
 このテーブルは、 **msdb**データベースに格納されます。  

  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**folderid**|**UNIQUEIDENTIFIER**|フォルダーの GUID。|  
|**parentfolderid**|**UNIQUEIDENTIFIER**|親フォルダーであるフォルダーの GUID。|  
|**名**|**sysname**|フォルダーの名前。 これは、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] でフォルダー階層に表示される名前です。|  
  
  
