---
title: Sp_helptrigger 出力の列を新しいアプリケーションに影響を与える可能性があります |Microsoft Docs
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
- sp_helptrigger
ms.assetid: b7c42a8f-f2e0-4fa3-b046-3cf39c854c47
caps.latest.revision: 18
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8d8cb7b6623cd15e2e7617a1ae63baeaebe4e375
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37306992"
---
# <a name="new-column-in-output-of-sphelptrigger-may-impact-applications"></a>sp_helptrigger 出力の新しい列がアプリケーションに影響を与える可能性がある
  結果セットの最後の列は、sp_helptrigger システムによって返される trigger_schemaias はストアド プロシージャです。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]特定のテーブルで定義されるトリガーに関する情報を入手するには、sys.triggers カタログ ビューをクエリしてください。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>修正措置  
 アプリケーションで sp_helptrigger の使用を確認してください。 また、追加列に対応するようにアプリケーションを変更しなければならない場合があります。 代わりに、sys.triggers カタログ ビューを使用できます。  
  
## <a name="see-also"></a>参照  
 [データベース エンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 アップグレード アドバイザー&#91;新規&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
