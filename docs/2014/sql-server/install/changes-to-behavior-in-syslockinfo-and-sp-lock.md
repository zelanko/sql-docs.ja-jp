---
title: Syslockinfo および sp_lock での動作の変更 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- syslockinfo
- sp_lock
ms.assetid: b9892ae3-ac15-48be-8b52-78dbed6467ed
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e8c6534449ffc4e89efcd49c943726bf6ecd9f26
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66096647"
---
# <a name="changes-to-behavior-in-syslockinfo-and-sp_lock"></a>syslockinfo および sp_lock の動作に対する変更
  **syslockinfo**と**sp_lock**は、予期しない値を返すことがあります。 また、追加の行が返される場合もあります。一方、 **syslockinfo**と**sp_lock**の以前のバージョンでは、ロックリソースあたり最大2行が返されていました。  
  
 **Syslockinfo**から情報にアクセスしたり、 **sp_lock**を実行したりするには、サーバーに対する VIEW server STATE 権限が必要です。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>説明  
 で[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]は、 **syslockinfo**の**rsc_objid**列と**rsc_indid**列、および**sp_lock**の**objid**列と**indid**列は、常にオブジェクト ID とインデックス ID を返します。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] では、値 0 が返される場合があります。  
  
 で[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]は、 **syslockinfo**と**sp_lock**は、1つのトランザクション内の特定のロックリソースに対して最大で2つの行を返します。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降では、ロックのパーティション分割が有効である場合、1 つのトランザクションで実行している同じリソースに対して複数行が返されることがあります。 返される行は最大 N + 1 行である場合があります。ここで、N は Cpu の数です。 さらに、同じリソースに対する GRANTED 要求および WAITING 要求を表示できます。[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] では、それらの要求を表示できませんでした。  
  
## <a name="permissions"></a>アクセス許可  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;新しい&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
