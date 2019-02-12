---
title: sysssispackagefolders (TRANSACT-SQL) |Microsoft Docs
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
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 7c1a5e117ee1c79b918f9785310b9b7c97671729
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56025823"
---
# <a name="sysssispackagefolders-transact-sql"></a>sysssispackagefolders (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  フォルダー階層内の論理フォルダーごとに 1 つの行データを格納する[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]を使用します。 これらのフォルダーは、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] に接続したときに [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の Object Explorer に一覧表示されます。 フォルダーには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] またはファイル システムに保存されているパッケージが一覧表示されます。  
  
 **Parentfolderid**列には、フォルダー階層がについて説明します。 フォルダー階層の上部にあるフォルダーに null 値が含まれています**parentfolderid**します。  
  
 **Foldername**列には、オブジェクト エクスプ ローラーで表示されるフォルダーの名前が含まれています。  
  
 このテーブルに格納されます、 **msdb**データベース。  

  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**folderid**|**uniqueidentifier**|フォルダーの GUID。|  
|**parentfolderid**|**uniqueidentifier**|親フォルダーの GUID。|  
|**foldername**|**sysname**|フォルダーの名前。 これは、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] でフォルダー階層に表示される名前です。|  
  
  
