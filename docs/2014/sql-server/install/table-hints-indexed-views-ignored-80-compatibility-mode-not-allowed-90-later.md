---
title: インデックス付きビュー定義内のテーブルヒントは80互換性モードでは無視され、90モード以降では許可されません |。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- query hints [SQL Server]
- indexed views [SQL Server], query hints
ms.assetid: 405dfcff-a3a6-4e6d-a53a-ed77bbacdd13
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 69a6bae06b1cb5d7a727ff2582f10bccf1e21ca8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66091807"
---
# <a name="table-hints-in-indexed-view-definitions-are-ignored-in-80-compatibility-mode-and-are-not-allowed-in-90-mode-or-later"></a>インデックス付きビュー定義のテーブル ヒントが互換性モード 80 では無視され、互換性モード 90 以上では許可されない
  互換性モード 90 以上では、インデックス付きビューの定義のテーブル ヒントは使用できません。 詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「インデックス付きビューのデザイン」、「インデックス付きビューの作成」、および「クエリ ヒント ([!INCLUDE[tsql](../../includes/tsql-md.md)])」を参照してください。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>修正措置  
 テーブル ヒントは、インデックス付きビューの定義から削除する必要があります。 どの互換性モードを使用しているかにかかわらず、アプリケーションをテストすることをお勧めします。 アプリケーションをテストすることによって、インデックス付きビューがクエリに一致した場合など、インデックス付きビューが作成、更新、アクセスされたときに想定どおりに実行されるかどうかを確認できます。  
  
## <a name="see-also"></a>参照  
 [データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;新しい&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
