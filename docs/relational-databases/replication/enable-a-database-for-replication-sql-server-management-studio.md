---
title: レプリケーションのデータベースの有効化 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server replication]
ms.assetid: 8092faa3-9cff-4f81-926c-6a0070d1ce2c
caps.latest.revision: 33
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b08df5d4c7b8fe00bbbb56ff3ec0765a89ffd0c8
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37359964"
---
# <a name="enable-a-database-for-replication-sql-server-management-studio"></a>レプリケーションのデータベースの有効化 (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  固定サーバー ロール **sysadmin** のメンバーがパブリケーションの新規作成ウィザードでパブリケーションを作成すると、レプリケーションのデータベースが暗黙的に有効になります。 固定サーバー ロール **sysadmin** のメンバーは、レプリケーションのデータベースを明示的に有効にすることもできます。これにより、固定データベース ロール **db_owner** のメンバーが、そのデータベース内に 1 つ以上のパブリケーションを作成できるようになります。 データベースを明示的に有効にするには、**[パブリッシャーのプロパティ - \<Publisher>]** ボックスの **[パブリケーション データベース]** ページを使用します。 このダイアログ ボックスへのアクセスの詳細については、「 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)」を参照してください。  
  
### <a name="to-enable-a-database-for-replication"></a>レプリケーションのデータベースを有効化するには  
  
1.  **[パブリッシャーのプロパティ - \<Publisher>]** ダイアログ ボックスの **[パブリケーション データベース]** ページで、レプリケートする各データベースの **[トランザクション]** チェック ボックスまたは **[マージ]** チェック ボックスをオンにします。 スナップショット レプリケーションのデータベースを有効にするには、 **[トランザクション]** を選択します。  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
  
