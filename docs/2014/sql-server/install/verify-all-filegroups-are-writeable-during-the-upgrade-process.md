---
title: アップグレード処理中にすべてのファイルグループが書き込み可能であることを確認する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- filegroups [SQL Server], writeable
- writeable filegroups [SQL Server]
ms.assetid: 2985efc1-4b14-46c3-abbd-a656b159f23c
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 8146efb876bf97c36c549a2b58d104592df611e9
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85062315"
---
# <a name="verify-all-filegroups-are-writeable-during-the-upgrade-process"></a>アップグレード処理中にすべてのファイル グループが書き込み可能であることを確認する
  アップグレード アドバイザーによって、1 つ以上の読み取り専用のファイル グループを含むデータベースが検出されました。 アップグレードする前に、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンス内のすべてのデータベースでファイル グループを READ_WRITE に設定しておく必要があります。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>修正措置  
 ALTER DATABASE を使用してファイル グループを READ_WRITE に設定してください。  
  
## <a name="see-also"></a>参照  
 [データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;新しい&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
