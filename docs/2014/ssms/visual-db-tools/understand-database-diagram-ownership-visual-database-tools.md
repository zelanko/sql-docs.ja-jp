---
title: データベース ダイアグラムの所有権について (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- vdt.diagnostic.CannotOpenWithInvalidOwner
helpviewer_keywords:
- diagrams [SQL Server], ownership
- database diagrams [SQL Server], ownership
- owners [SQL Server], database diagrams
ms.assetid: 4a27a48e-c4ef-4017-82b8-0cac4d0bbcac
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0fef70305887b7d0b2d5face1dc31a2e7ea451c6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48102452"
---
# <a name="understand-database-diagram-ownership-visual-database-tools"></a>データベース ダイアグラムの所有権について (Visual Database Tools)
  データベース ダイアグラム デザイナーを使用するには、db_owner ロール ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースのロール) のメンバーが、ダイアグラムへのアクセスを制御するようにあらかじめ設定しておく必要があります。 各ダイアグラムの所有者は 1 人だけで、ダイアグラムを作成したユーザーが所有者になります。 ダイアグラムの設定の詳細についてを参照してください。[データベース ダイアグラム デザイナーの設定&#40;Visual Database Tools&#41;](visual-database-tools.md)します。  
  
 ダイアグラムの所有権については、次の点に注意してください。  
  
-   データベースへのアクセス権を持つユーザーであればだれでもダイアグラムを作成できますが、作成されたダイアグラムを表示できるユーザーは、ダイアグラムの作成者と db_owner ロールのメンバーだけです。  
  
-   ダイアグラムの所有権は、db_owner ロールのメンバーだけに移譲できます。 移譲できるのは、ダイアグラムの前の所有者がデータベースから削除された場合だけです。  
  
-   ダイアグラムの所有者がデータベースから削除されても、db_owner ロールのメンバーが開こうとするまでダイアグラムはデータベース内に残ります。 ダイアグラムを開く時点で、db_owner メンバーはダイアグラムの所有権を継承するかどうかを選択できます。  
  
## <a name="see-also"></a>参照  
 [データベース ダイアグラムを扱う&#40;Visual Database Tools&#41;](work-with-database-diagrams-visual-database-tools.md)   
 [データベース ダイアグラム デザイナーの設定 (Visual Database Tools)](visual-database-tools.md)  
  
  
