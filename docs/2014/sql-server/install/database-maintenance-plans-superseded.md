---
title: データベースメンテナンスプランの置き換え |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- suspended database maintenance plans
- database maintenance plans [SQL Server Agent]
- maintenance plans [SQL Server Agent]
ms.assetid: efac127c-6c81-4c7a-a6c4-9aae5d15545d
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7d41763582632a92b3a38bdbd67ee55b65f95b6d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66095762"
---
# <a name="database-maintenance-plans-superseded"></a>データベース メンテナンス プランが新しくなった
    
## <a name="component"></a>コンポーネント  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント  
  
## <a name="description"></a>説明  
 既存のデータベース メンテナンス プランはアップグレードされ、引き続き機能します。 ただし、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して新しいデータベース メンテナンス プランを作成することはできません。 オブジェクト エクスプローラーでメンテナンス プランを表示するには、[管理]、[レガシ] の順に展開します。 既存のデータベースメンテナンスプランを新しい形式に移行するには、任意のデータベースメンテナンスプランのコンテキストメニューから [**移行**] を選択します。 新しいメンテナンス プランの機能がデータベース メンテナンス プランとそのまま置き換わるわけではないため、移行後に機能の一部が失われる可能性があります。 データベース メンテナンス プランを移行しても古いプランは削除されません。このため、古いプランを削除する前にメンテナンス プランとしての機能をテストできます。  
  
 次の機能は、データベース メンテナンス プラン内ではサポートされなくなります。  
  
-   ログ配布  
  
-   **データベースの整合性チェック**タスクの**軽微な問題を修復しようとしまし**た  
  
## <a name="corrective-action"></a>修正措置  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、ログ配布をデータベース メンテナンス プランに含めることができません。 詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「ログ配布」を参照してください。  
  
  
