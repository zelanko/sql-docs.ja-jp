---
title: アップグレード処理中にすべてのファイル グループが書き込み可能なことを確認 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- filegroups [SQL Server], writeable
- writeable filegroups [SQL Server]
ms.assetid: 2985efc1-4b14-46c3-abbd-a656b159f23c
caps.latest.revision: 20
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 41ca2adb014d1cdaee23e32123772744fae76b68
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37328972"
---
# <a name="verify-all-filegroups-are-writeable-during-the-upgrade-process"></a>アップグレード処理中にすべてのファイル グループが書き込み可能であることを確認する
  アップグレード アドバイザーによって、1 つ以上の読み取り専用のファイル グループを含むデータベースが検出されました。 アップグレードする前に、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンス内のすべてのデータベースでファイル グループを READ_WRITE に設定しておく必要があります。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>修正措置  
 ALTER DATABASE を使用してファイル グループを READ_WRITE に設定してください。  
  
## <a name="see-also"></a>参照  
 [データベース エンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 アップグレード アドバイザー&#91;新規&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
