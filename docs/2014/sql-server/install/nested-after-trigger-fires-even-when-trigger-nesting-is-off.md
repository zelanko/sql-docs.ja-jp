---
title: 入れ子になった AFTER トリガーは、トリガーの入れ子が OFF の場合でも起動されます。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- DML triggers, nested
- nested triggers option
- triggers [SQL Server], nested
ms.assetid: 94d72960-676e-40d9-81bc-08bffe778110
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f91c04e8d69880b451c1479e2907cd1910e8f9c1
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85042124"
---
# <a name="nested-after-trigger-fires-even-when-trigger-nesting-is-off"></a>トリガーの入れ子がオフになっている場合でも、入れ子になった AFTER トリガーが起動される
  アップグレード アドバイザーによって、1 つ以上のテーブルで定義されている INSTEAD OF トリガー内に入れ子になった AFTER トリガーが検出されました。 入れ子になった AFTER トリガーは、`nested triggers` サーバー構成オプションが 0 に設定されている場合でも起動されることがあります。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>説明  
 INSTEAD OF トリガー内で入れ子になっている最初の AFTER トリガーは、 `nested triggers` サーバー構成オプションが0に設定されている場合でも起動されます。 ただし、この設定では、後続の AFTER トリガーは起動されません。  
  
## <a name="corrective-action"></a>修正措置  
 アプリケーションに入れ子になったトリガーがないかどうかを調査し、`nested triggers` サーバー構成オプションが 0 に設定されている場合の新しい動作に関して、アプリケーションがビジネス ルールに従っているかどうかを判断します。その後、適切な変更を加えてください。  
  
## <a name="see-also"></a>参照  
 [データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;新しい&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
