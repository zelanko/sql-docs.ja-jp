---
title: データベース ダイアグラムの所有権について (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
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
ms.openlocfilehash: 7aeb291651fb79a766c120fec6eadf43a7c8bbf7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47717600"
---
# <a name="understand-database-diagram-ownership-visual-database-tools"></a>データベース ダイアグラムの所有権について (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
データベース ダイアグラム デザイナーを使用するには、db_owner ロール ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースのロール) のメンバーが、ダイアグラムへのアクセスを制御するようにあらかじめ設定しておく必要があります。 各ダイアグラムの所有者は 1 人だけで、ダイアグラムを作成したユーザーが所有者になります。 ダイアグラムの設定の詳細については、「 [データベース ダイアグラム デザイナーの設定 (Visual Database Tools)](../../ssms/visual-db-tools/set-up-database-diagram-designer-visual-database-tools.md)」をご覧ください。  
  
ダイアグラムの所有権については、次の点に注意してください。  
  
-   データベースへのアクセス権を持つユーザーであればだれでもダイアグラムを作成できますが、作成されたダイアグラムを表示できるユーザーは、ダイアグラムの作成者と db_owner ロールのメンバーだけです。  
  
-   ダイアグラムの所有権は、db_owner ロールのメンバーだけに移譲できます。 移譲できるのは、ダイアグラムの前の所有者がデータベースから削除された場合だけです。  
  
-   ダイアグラムの所有者がデータベースから削除されても、db_owner ロールのメンバーが開こうとするまでダイアグラムはデータベース内に残ります。 ダイアグラムを開く時点で、db_owner メンバーはダイアグラムの所有権を継承するかどうかを選択できます。  
  
## <a name="see-also"></a>参照  
[データベース ダイアグラムの使用 (Visual Database Tools)](../../ssms/visual-db-tools/work-with-database-diagrams-visual-database-tools.md)  
[データベース ダイアグラム デザイナーの設定 (Visual Database Tools)](../../ssms/visual-db-tools/set-up-database-diagram-designer-visual-database-tools.md)  
  
