---
title: 運用されているデータベースを変更するときの問題 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- compatibility [SQL Server], multuser database changes
- database evolution [SQL Server]
ms.assetid: 1ed6ae10-d212-4ec2-8569-1b94ab1cba6d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d3a1f10ae77061983a5cf64ddd5a3462bb4be49b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63035591"
---
# <a name="issues-of-database-evolution-visual-database-tools"></a>運用されているデータベースを変更するときの問題 (Visual Database Tools)
  配置されているデータベースの構成を変更する場合は、既存のデータおよびデータベース構成との互換性を保って変更を行うよう、特別な注意を払う必要があります。 次の変更を行うときは、特別な手順が必要になる場合があります。  
  
-   **制約の追加**制約を追加した場合、データベースにはそれを満たしていないデータが既に含まれている可能性があります。 新しい制約を保存しようとすると、[[保存前の通知] ダイアログ ボックス (Visual Database Tools)](visual-database-tools.md) が表示されて、データベース サーバーが新しい制約を作成できないことが通知されます。 新しい制約をデータベースに強制的に設定するには、**[作成時に既存データを確認する]** チェック ボックスをオフにします。  
  
-   **リレーションシップの追加**リレーションシップを追加すると、主キーテーブルに対応する行がない外部キーテーブルの行がデータベースに既に含まれている可能性があります。 つまり、既存のデータが参照整合性を満たしていない可能性があります。 新しいリレーションシップを保存しようとすると、[[保存前の通知] ダイアログ ボックス (Visual Database Tools)](visual-database-tools.md) が表示されて、データベース サーバーが変更された外部キー テーブルを作成できないことが通知されます。 変更をデータベースに強制的に保存するには、**[作成時に既存データを確認する]** チェック ボックスをオフにします。  
  
-   **インデックス付きビューに寄与するテーブルの変更**Microsoft SQL Server インデックス付きビューに寄与するテーブルを変更すると、ビューのインデックスは失われます。 インデックスの作成方法については、『SQL Server オンライン ブック』を参照してください。  
  
-   **オブジェクトの削除**列、テーブル、またはビューなどのオブジェクトを削除する場合は、まず、そのオブジェクトがデータベース内の別のオブジェクトによって参照されていないことを確認してください。  
  
 データベースのデザインを変更する場合は常に、変更の履歴を残しておく必要があります。 1 つの方法として、実行時用データベースに対して行ったすべての変更について、SQL スクリプトを残しておくことができます。  
  
## <a name="see-also"></a>参照  
 [Unique 制約と Check 制約](../../relational-databases/tables/unique-constraints-and-check-constraints.md)   
 [マルチユーザー環境 (Visual Database Tools)](multiuser-environments-visual-database-tools.md)  
  
  
