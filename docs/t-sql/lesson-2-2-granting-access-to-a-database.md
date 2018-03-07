---
title: "データベースにアクセス権の付与 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- database access
ms.assetid: 686edfe2-3650-48a6-a2da-9d46fa211ad8
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 50badd521bde0d30021f7097040beb8492cb1d2e
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="lesson-2-2---granting-access-to-a-database"></a>レッスン 2-2-データベースへのアクセスを許可します。
[!INCLUDE[tsql-appliesto-ss2008-all-md](../includes/tsql-appliesto-ss2008-all-md.md)]Mary のこのインスタンスへのアクセスを持つようになりました[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]データベースにアクセスする権限はありません。 データベースのユーザーとして承認されるまでは、既定の **TestData** データベースにさえアクセスできません。  
  
Mary にアクセス権を与えるには、 **TestData** データベースに切り替えてから CREATE USER ステートメントを使用して、Mary という名のユーザーにそのログインをマップします。  
  
### <a name="to-create-a-user-in-a-database"></a>データベースにユーザーを作成するには  
  
1.  次のステートメントを入力して実行し ( `computer_name` をコンピューターの名前に置き換える)、 `Mary` に `TestData` データベースへのアクセス権を与えます。  
  
    ```  
    USE [TestData];  
    GO  
  
    CREATE USER [Mary] FOR LOGIN [computer_name\Mary];  
    GO  
  
    ```  
  
    これで、Mary は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] と `TestData` の両方のデータベースにアクセスできます。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
[ビューとストアド プロシージャの作成](../t-sql/lesson-2-3-creating-views-and-stored-procedures.md)  
  
  
  
