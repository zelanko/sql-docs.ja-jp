---
title: マスター サーバーをアップグレードする前にすべての対象サーバーのアップグレード |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- TSX [SQL Server Agent]
- target servers [SQL Server Agent]
- MSX [SQL Server Agent]
- master servers [SQL Server Agent]
ms.assetid: 2c231793-3878-4a5e-a425-1fa0d787ba84
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 97272209c1ceba780711ecf4a07178ddf8943d49
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48061954"
---
# <a name="upgrade-all-target-servers-before-upgrading-the-master-server"></a>マスター サーバーをアップグレードする前にすべての対象サーバーをアップグレードする
  マスター サーバーをアップグレードする前に、対象サーバーとして構成され、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行しているすべてのコンピューターをアップグレードしてください。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント  
  
## <a name="description"></a>説明  
 マルチサーバー環境で管理を自動化するには、マスター サーバーとターゲット サーバーが少なくとも 1 台ずつ必要です。 マスター サーバーは、対象サーバーに対してジョブを分散し、対象サーバーからイベントを受け取ります。 また、マスター サーバーは、対象サーバーで実行されるジョブについて、ジョブ定義の中央コピーも保存します。  
  
 現在のサーバーがマスター サーバーとして構成されている場合、最初にすべての対象サーバーをアップグレードしてから、マスター サーバーをアップグレードしてください。  
  
## <a name="corrective-action"></a>修正措置  
 マスター サーバーをアップグレードする前に、すべての対象サーバーをアップグレードできない場合は、アップグレード後に、すべての対象サーバーの参加を解除してからもう一度参加させる必要があります。  
  
 詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックのトピック「エンタープライズ全体の管理の自動化」、「マスター サーバーからターゲット サーバーの参加を解除する方法」、および「マスター サーバーにターゲット サーバーを参加させる方法」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQL Server エージェントのアップグレードに関する問題](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)   
 [SQL Server エージェントのアップグレードに関する問題](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
