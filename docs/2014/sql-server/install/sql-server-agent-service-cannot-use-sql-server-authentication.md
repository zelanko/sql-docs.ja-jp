---
title: SQL Server エージェント サービスは、SQL Server 認証を使用できない |Microsoft Docs
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
- authentication [SQL Server Agent]
- SQL Server Authentication [SQL Server Agent]
ms.assetid: c39f3ec3-fc2c-4c12-940f-60d8d3d17660
caps.latest.revision: 19
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 263f3e865a59b215ccbfc0382958dffe5cfb518e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37238262"
---
# <a name="sql-server-agent-service-cannot-use-sql-server-authentication"></a>SQL Server エージェント サービスで SQL Server 認証を使用できない
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続する場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントは Windows 認証のみをサポートします。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント  
  
## <a name="description"></a>説明  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスは、Windows 認証を使用してデータベースにログオンすることのみできます。 つまり、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービス アカウントは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーザーである必要があります。  
  
 詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「SQL Server エージェントのセキュリティ管理」および「[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのセキュリティの実装」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQL Server エージェントのアップグレードに関する問題](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
