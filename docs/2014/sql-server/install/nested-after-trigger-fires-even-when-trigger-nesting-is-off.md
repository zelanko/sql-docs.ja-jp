---
title: トリガーの入れ子が OFF の場合に入れ子になった AFTER トリガーが起動されます |Microsoft Docs
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
- DML triggers, nested
- nested triggers option
- triggers [SQL Server], nested
ms.assetid: 94d72960-676e-40d9-81bc-08bffe778110
caps.latest.revision: 21
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 683ffcfa3bb4715b25fb912fa12808be3b0873ec
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37247832"
---
# <a name="nested-after-trigger-fires-even-when-trigger-nesting-is-off"></a>トリガーの入れ子がオフになっている場合でも、入れ子になった AFTER トリガーが起動される
  アップグレード アドバイザーによって、1 つ以上のテーブルで定義されている INSTEAD OF トリガー内に入れ子になった AFTER トリガーが検出されました。 入れ子になった AFTER トリガーは、`nested triggers` サーバー構成オプションが 0 に設定されている場合でも起動されることがあります。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>説明  
 最初の AFTER トリガーが INSTEAD OF トリガーが起動場合であっても内部で入れ子になった、`nested triggers`サーバー構成オプションが 0 に設定します。 ただし、この設定では、後続の AFTER トリガーは起動されません。  
  
## <a name="corrective-action"></a>修正措置  
 アプリケーションに入れ子になったトリガーがないかどうかを調査し、`nested triggers` サーバー構成オプションが 0 に設定されている場合の新しい動作に関して、アプリケーションがビジネス ルールに従っているかどうかを判断します。その後、適切な変更を加えてください。  
  
## <a name="see-also"></a>参照  
 [データベース エンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 アップグレード アドバイザー&#91;新規&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
