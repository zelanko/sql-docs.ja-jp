---
title: アップグレード処理中に、圧縮されたドライブにデータベースファイルがないことを確認する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- compressed drives [SQL Server]
ms.assetid: 63be6853-c54a-42b2-ae1a-db2175f1d28e
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 41c183c72188cccb21838e1e574992bfb723c022
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66091157"
---
# <a name="verify-that-no-database-files-are-on-compressed-drives-during-the-upgrade-process"></a>アップグレード処理中にデータベース ファイルが圧縮ドライブにないことを確認する
  アップグレード アドバイザーが圧縮ドライブにデータベース ファイルを検出しました。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、圧縮ドライブにデータベースを作成できません。圧縮ドライブのデータベースをアップグレードすることもできません。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>修正措置  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をインストールするとき、システム データベースの保存場所として圧縮されていないドライブを選択します。また、アップグレード対象のデータベースが、圧縮ドライブに格納されていないことを確認してください。 ただし、データベースをアップグレードした後は、読み取り専用データベースと読み取り専用セカンダリ ファイル グループを NTFS 圧縮ファイル システムに配置できます。  
  
## <a name="see-also"></a>参照  
 [データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;新しい&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
