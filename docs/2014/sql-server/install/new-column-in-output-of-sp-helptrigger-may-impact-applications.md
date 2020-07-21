---
title: Sp_helptrigger の出力の新しい列がアプリケーションに影響を与える可能性があります |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- sp_helptrigger
ms.assetid: b7c42a8f-f2e0-4fa3-b046-3cf39c854c47
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0b1f5e936843ed84a5c6b88e2f3685e7a4272bc2
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85012170"
---
# <a name="new-column-in-output-of-sp_helptrigger-may-impact-applications"></a>sp_helptrigger 出力の新しい列がアプリケーションに影響を与える可能性がある
  sp_helptrigger システムストアドプロシージャによって返される結果セットの最後の列を trigger_schemaias します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]特定のテーブルで定義されるトリガーに関する情報を入手するには、sys.triggers カタログ ビューをクエリしてください。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>修正措置  
 アプリケーションで sp_helptrigger の使用を確認してください。 また、追加列に対応するようにアプリケーションを変更しなければならない場合があります。 代わりに、sys.triggers カタログ ビューを使用できます。  
  
## <a name="see-also"></a>参照  
 [データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;新しい&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
