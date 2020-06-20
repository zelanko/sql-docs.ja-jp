---
title: 無効な名前付きパイプ名を使用してアップグレードをブロックすることができます |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- invalid named pipes [SQL Server]
- named pipes
ms.assetid: 58c2199c-4fdf-4d43-ac1c-842703344b75
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: bacfd3d097d7cccb0a5780328c4db95dc5afc733
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059250"
---
# <a name="invalid-named-pipe-name-can-block-upgrade"></a>無効な名前付きパイプ名によってアップグレードがブロックされる
  アップグレードは、名前付きパイプのプロトコルの構成が正しくない場合は失敗します。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>説明  
 アップグレード中、セットアッププログラムは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 共有メモリサポート (ローカル接続のみを受け入れる名前付きパイプ) を使用してインスタンスを起動します。 サーバーで指定されているパイプ名が空白でない場合は、文字列 "て .\pipe" で始まる必要があり \\ \\ \\ ます。 パイプ名が有効でない場合、[!INCLUDE[ssDE](../../includes/ssde-md.md)]が起動せず、セットアップは失敗します。  
  
## <a name="corrective-action"></a>修正措置  
 ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ネットワークユーティリティ**を使用して有効なパイプ名を指定してから、セットアップを実行してください。  
  
## <a name="see-also"></a>参照  
 [データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;新しい&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
