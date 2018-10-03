---
title: トレース フラグの動作の変更 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- trace flags [SQL Server], behavior changes
ms.assetid: d739df96-2659-4383-8e10-194657632526
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fe5d7e5580fb59616dbde50244bf1b45e94d2dfb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48104532"
---
# <a name="changes-to-behavior-of-trace-flags"></a>トレース フラグの動作が変更された
  あるセッションによって設定されたグローバル トレース フラグは他のセッションですぐに有効になります。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] には、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の一部のトレース フラグが存在しません。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>説明  
 アップグレードする前に、すべてのトレース フラグを無効にすることをお勧めします。 データベースの可用性または復旧モードを変更するトレース フラグができない場合があります、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスを正常にアップグレードした[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 トレース フラグが必要になり、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] でも有効であることを確認した後、トレース フラグを有効にできます。 トレース フラグを再び有効にするには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスで追加テストを実行する必要があります。  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] は、グローバル トレース フラグとセッション レベルのトレース フラグをサポートしています。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] の場合、DBCC TRACEON コマンドに引数 (-1) を追加することによって、ローカル、グローバルのいずれでもトレース フラグを指定できます。 この引数を指定しない場合、既定値はローカルになります。  
  
 また、[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] では、セッション A で設定されたトレース フラグは、既に存在するセッション B では自動的に有効になりません。代わりに、セッション B に初めてトレース フラグが設定された後にのみ有効になります。この動作は [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] では非決定的であり、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンでは決定的です。 以降のバージョンでは、セッション A で設定されたトレース フラグは、他の同時セッションに直ちに設定されます。  
  
## <a name="see-also"></a>参照  
 [データベース エンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 アップグレード アドバイザー&#91;新規&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
