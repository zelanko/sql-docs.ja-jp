---
title: "テーブルのスクリプト作成 | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-tutorial
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea88d736-849e-4368-b55d-06aeee097bf3
caps.latest.revision: "31"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 6bb5dde877470ede338eabbcf3effd4b3ebc5444
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="lesson-2-6---script-a-table"></a>レッスン 2-6 - テーブルのスクリプト作成
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] では、テーブルを選択、挿入、更新、削除するスクリプト、およびストアド プロシージャを作成、変更、削除、または実行するスクリプトを作成できます。  
  
プロシージャを削除した後でプロシージャを作成したり、テーブルを作成した後でテーブルを変更するなど、1 つのスクリプトで複数のオプションを実行させたい場合もあります。 複合的なスクリプトを作成するには、1 番目のスクリプトをクエリ エディター ウィンドウに保存し、2 番目のスクリプトをクリップボードに保存します。次に、クエリ エディター ウィンドウで、1 番目のスクリプトの後ろに 2 番目のスクリプトを貼り付けます。  
  
 
1.  オブジェクト エクスプローラーでサーバーを展開し、 **[データベース]**、[ [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]]、 **[テーブル]**の順に展開します。次に、 **[HumanResources.Employee]**を右クリックし、 **[テーブルをスクリプト化]**をポイントします。  
  
2.  ショートカット メニューには、 **[新規作成]**、 **[削除]**、 **[削除および作成]**、 **[検索]**、 **[データ登録]**、 **[データ更新]**、 **[データ削除]**という 7 つの使用可能なスクリプト オプションがあります。 **[データ更新]**をポイントし、 **[新しいクエリ エディター ウィンドウ]**をクリックします。  
  
3.  新しいクエリ エディター ウィンドウが開き、接続が確立され、更新ステートメント全体が表示されます。  
  
    この実習では、テーブルやストアド プロシージャを作成する以外にスクリプト機能でどのようなことを実行できるのかを学習します。 この新機能により、データ操作スクリプトをプロジェクトにすばやく追加し、スクリプトによるストアド プロシージャの実行を簡単に行うことができます。 多数のフィールドを持つテーブルやプロシージャでは、時間を大幅に節約できます。  
  
 
  
  
  
