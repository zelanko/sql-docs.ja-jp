---
title: クエリの検査 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-visual-db
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:100644
helpviewer_keywords:
- verifying queries
- queries [SQL Server], verifying
- checking queries
ms.assetid: 1382c0c0-46dc-45f9-ab38-9bba1d347eea
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3848b8cc758dde890c06711b4bea4e70cd137bb2
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38052990"
---
# <a name="verify-queries-visual-database-tools"></a>クエリの検査 (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
問題を回避するために、作成したクエリを検証して、構文が正しいことを確認できます。 このオプションは、 [SQL ペイン](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md)にステートメントを入力する場合に特に便利です。  
  
次に、クエリの検査について注意が必要な点を挙げます。  
  
-   **ダイアグラム ペイン** および **抽出条件ペイン**に表示できない場合でも、有効なステートメントは正しく検査されます。  
  
-   SQL 検査では SQL エラーのすべてが検出されるわけではありません。 SQL 検査で検出されないエラーがクエリにある場合は、クエリを実行するときに、データベースによってエラーが検出されます。  
  
-   パラメーターを含むクエリは検査できません。  
  
### <a name="to-verify-an-sql-statement"></a>SQL ステートメントを検査するには  
  
-   **SQL ペイン**を右クリックし、ショートカット メニューの **[SQL 構文の確認]** を選択します。  
  
## <a name="see-also"></a>参照  
[クエリの実行 (Visual Database Tools)](../../ssms/visual-db-tools/run-queries-visual-database-tools.md)  
[クエリに関する基本操作の実行 (Visual Database Tools)](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  
