---
title: システム オブジェクトに対する列レベルのアクセス許可を変更するステートメントの削除 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- column-level permissions [SQL Server]
- removed statement permissions [SQL Server]
ms.assetid: 7f4fbbef-2696-4911-903b-63f6d9e4484a
caps.latest.revision: 21
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 217feecec3058c71a51914bde1db9e20755472db
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37316122"
---
# <a name="remove-statements-that-modify-column-level-permissions-on-system-objects"></a>システム オブジェクトの列レベル権限を変更するステートメントを削除する
  アップグレード アドバイザーがシステム オブジェクトに対する標準以外の列レベル権限を検出しました。 これらの権限の変更は、アップグレードすると維持されません。 また、システム オブジェクトに対する列レベル権限はサポートされません。 アプリケーションから、システム オブジェクトに対する列レベル権限を設定するステートメントを削除してください。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>修正措置  
 システム オブジェクトに対する列レベル権限を許可、拒否、または禁止するステートメントをアプリケーションから削除します。  
  
## <a name="see-also"></a>参照  
 [データベース エンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 アップグレード アドバイザー&#91;新規&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
