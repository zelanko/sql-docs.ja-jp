---
title: 内のテーブル ヒントにインデックス付きビューの定義は、互換性モード 80 では無視され、モードが 90 以上では許可されません |Microsoft Docs
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
- query hints [SQL Server]
- indexed views [SQL Server], query hints
ms.assetid: 405dfcff-a3a6-4e6d-a53a-ed77bbacdd13
caps.latest.revision: 22
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 93159a8c32f484fd9c734b4847dfd1e7fca854a8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37317432"
---
# <a name="table-hints-in-indexed-view-definitions-are-ignored-in-80-compatibility-mode-and-are-not-allowed-in-90-mode-or-later"></a>インデックス付きビュー定義のテーブル ヒントが互換性モード 80 では無視され、互換性モード 90 以上では許可されない
  互換性モード 90 以上では、インデックス付きビューの定義のテーブル ヒントは使用できません。 詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「インデックス付きビューのデザイン」、「インデックス付きビューの作成」、および「クエリ ヒント ([!INCLUDE[tsql](../../includes/tsql-md.md)])」を参照してください。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>修正措置  
 テーブル ヒントは、インデックス付きビューの定義から削除する必要があります。 どの互換性モードを使用しているかにかかわらず、アプリケーションをテストすることをお勧めします。 アプリケーションをテストすることによって、インデックス付きビューがクエリに一致した場合など、インデックス付きビューが作成、更新、アクセスされたときに想定どおりに実行されるかどうかを確認できます。  
  
## <a name="see-also"></a>参照  
 [データベース エンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 アップグレード アドバイザー&#91;新規&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
