---
title: "運用されているデータベースを変更するときの問題 (Visual Database Tools) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- compatibility [SQL Server], multuser database changes
- database evolution [SQL Server]
ms.assetid: 1ed6ae10-d212-4ec2-8569-1b94ab1cba6d
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 42a9d7cc9821492e84e7dd8e95fcf1e84be09734
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="issues-of-database-evolution-visual-database-tools"></a>運用されているデータベースを変更するときの問題 (Visual Database Tools)
配置されているデータベースの構成を変更する場合は、既存のデータおよびデータベース構成との互換性を保って変更を行うよう、特別な注意を払う必要があります。 次の変更を行うときは、特別な手順が必要になる場合があります。  
  
-   **制約の追加** 制約を追加する場合、その制約を満たさないデータがデータベースに既に存在している可能性があります。 新しい制約を保存しようとすると、[[保存前の通知] ダイアログ ボックス (Visual Database Tools)](../../ssms/visual-db-tools/post-save-notifications-dialog-box-visual-database-tools.md) が表示されて、データベース サーバーが新しい制約を作成できないことが通知されます。 新しい制約をデータベースに強制的に設定するには、**[作成時に既存データを確認する]** チェック ボックスをオフにします。  
  
-   **リレーションシップの追加** リレーションシップを作成する場合、主キー テーブルの行に対応していない外部キー テーブルの行が既に存在している可能性があります。 つまり、既存のデータが参照整合性を満たしていない可能性があります。 新しいリレーションシップを保存しようとすると、[[保存前の通知] ダイアログ ボックス (Visual Database Tools)](../../ssms/visual-db-tools/post-save-notifications-dialog-box-visual-database-tools.md) が表示されて、データベース サーバーが変更された外部キー テーブルを作成できないことが通知されます。 変更をデータベースに強制的に保存するには、**[作成時に既存データを確認する]** チェック ボックスをオフにします。  
  
-   **インデックス付きビューに含まれるテーブルの変更** Microsoft SQL Server のインデックス付きビューに含まれるテーブルを変更すると、ビューのインデックスが失われます。 インデックスの作成方法については、『SQL Server オンライン ブック』を参照してください。  
  
-   **オブジェクトの削除** 列、テーブル、またはビューなどのオブジェクトを削除する場合は、まずデータベース内の他のオブジェクトがそのオブジェクトを参照していないことを確認します。  
  
データベースのデザインを変更する場合は常に、変更の履歴を残しておく必要があります。 1 つの方法として、実行時用データベースに対して行ったすべての変更について、SQL スクリプトを残しておくことができます。  
  
## <a name="see-also"></a>参照  
[制約の使用 (Visual Database Tools)](http://msdn.microsoft.com/en-us/637098af-2567-48f8-90f4-b41df059833e)  
[マルチユーザー環境 (Visual Database Tools)](../../ssms/visual-db-tools/multiuser-environments-visual-database-tools.md)  
  

