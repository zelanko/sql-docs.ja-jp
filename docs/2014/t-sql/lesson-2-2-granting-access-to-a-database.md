---
title: データベース オブジェクトへのアクセス権の付与 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- database access
ms.assetid: 686edfe2-3650-48a6-a2da-9d46fa211ad8
caps.latest.revision: 11
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 2fb1db5b03e7379052e006c6c68d8cf1efd5404b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36077242"
---
# <a name="granting-access-to-a-database"></a>データベースへのアクセス権の付与
  これで Mary は [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のこのインスタンスにアクセスできますが、データベースにアクセスする権限がありません。 データベースのユーザーとして承認されるまでは、既定の **TestData** データベースにさえアクセスできません。  
  
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
 [ビューとストアド プロシージャの作成](lesson-2-3-creating-views-and-stored-procedures.md)  
  
  