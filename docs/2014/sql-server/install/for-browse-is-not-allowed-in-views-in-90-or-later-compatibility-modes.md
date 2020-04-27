---
title: 90以降の互換性モードでは、FOR BROWSE はビューで許可されていません。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- views [SQL Server], FOR BROWSE clause
- FOR BROWSE clause
ms.assetid: 8f49b1c1-d877-4c46-b988-f8cdd8ac0925
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4811a3df80257b1e2d0e903fad562568eeec4ea2
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66095181"
---
# <a name="for-browse-is-not-allowed-in-views-in-90-or-later-compatibility-modes"></a>互換性モードが 90 以上の場合、FOR BROWSE はビューで使用できません
  アップグレード アドバイザーは、ビューで FOR BROWSE 句が使用されているのを検出しました。 データベースの互換性モードが 80 に設定されている場合は、FOR BROWSE 句をビューで使用できます (ただし、無視されます)。 FOR BROWSE 句は、データベース互換性モードが 90 以上に設定されている場合、ビューで使用できません。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>修正措置  
 アップグレードすると、ユーザー データベースでは互換性モードが維持されます。 データベース互換性モードを 90 以上に変更する前に、ビュー定義から FOR BROWSE 句を削除します。 詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「sp_dbcmptlevel」を参照してください。  
  
## <a name="see-also"></a>参照  
 [データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;新しい&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
