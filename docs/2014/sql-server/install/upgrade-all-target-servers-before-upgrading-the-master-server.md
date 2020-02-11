---
title: マスターサーバーをアップグレードする前にすべての対象サーバーをアップグレードする |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
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
ms.openlocfilehash: 2b6e08a384e20d64a7002171059db0d35dfd94a7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66091472"
---
# <a name="upgrade-all-target-servers-before-upgrading-the-master-server"></a>マスター サーバーをアップグレードする前にすべてのターゲット サーバーをアップグレードする
  マスター サーバーをアップグレードする前に、ターゲット サーバーとして構成され、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行しているすべてのコンピューターをアップグレードしてください。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]・  
  
## <a name="description"></a>[説明]  
 マルチサーバー環境で管理を自動化するには、マスター サーバーとターゲット サーバーが少なくとも 1 台ずつ必要です。 マスター サーバーは、ターゲット サーバーに対してジョブを分散し、ターゲット サーバーからイベントを受け取ります。 また、マスター サーバーは、ターゲット サーバーで実行されるジョブについて、ジョブ定義の中央コピーも保存します。  
  
 現在のサーバーがマスター サーバーとして構成されている場合、最初にすべてのターゲット サーバーをアップグレードしてから、マスター サーバーをアップグレードしてください。  
  
## <a name="corrective-action"></a>修正措置  
 マスター サーバーをアップグレードする前に、すべてのターゲット サーバーをアップグレードできない場合は、アップグレード後に、すべてのターゲット サーバーの参加を解除してからもう一度参加させる必要があります。  
  
 詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックのトピック「エンタープライズ全体の管理の自動化」、「マスター サーバーからターゲット サーバーの参加を解除する方法」、および「マスター サーバーにターゲット サーバーを参加させる方法」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQL Server エージェントのアップグレードに関する問題](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)   
 [SQL Server エージェントのアップグレードに関する問題](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
