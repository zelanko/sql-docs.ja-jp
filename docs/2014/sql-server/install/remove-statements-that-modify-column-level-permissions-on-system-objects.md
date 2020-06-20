---
title: システムオブジェクトに対する列レベルの権限を変更するステートメントを削除する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- column-level permissions [SQL Server]
- removed statement permissions [SQL Server]
ms.assetid: 7f4fbbef-2696-4911-903b-63f6d9e4484a
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: e55af3dca0c55c2babd09bc6cfc48ed0ddf3ad7a
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059168"
---
# <a name="remove-statements-that-modify-column-level-permissions-on-system-objects"></a>システム オブジェクトの列レベル権限を変更するステートメントを削除する
  アップグレード アドバイザーがシステム オブジェクトに対する標準以外の列レベル権限を検出しました。 これらの権限の変更は、アップグレードすると維持されません。 また、システム オブジェクトに対する列レベル権限はサポートされません。 アプリケーションから、システム オブジェクトに対する列レベル権限を設定するステートメントを削除してください。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>修正措置  
 システム オブジェクトに対する列レベル権限を許可、拒否、または禁止するステートメントをアプリケーションから削除します。  
  
## <a name="see-also"></a>参照  
 [データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;新しい&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
