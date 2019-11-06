---
title: レプリケーションのデータベースの有効化 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server replication]
ms.assetid: 8092faa3-9cff-4f81-926c-6a0070d1ce2c
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: 8a52640a104af0030d0ebf51162e0efbda80d56a
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2019
ms.locfileid: "68768129"
---
# <a name="enable-a-database-for-replication-sql-server-management-studio"></a>レプリケーションのデータベースの有効化 (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  
固定サーバー ロール **sysadmin** のメンバーがパブリケーションの新規作成ウィザードでパブリケーションを作成すると、レプリケーションのデータベースが暗黙的に有効になります。 固定サーバー ロール **sysadmin** のメンバーは、レプリケーションのデータベースを明示的に有効にすることもできます。これにより、固定データベース ロール **db_owner** のメンバーが、そのデータベース内に 1 つ以上のパブリケーションを作成できるようになります。 データベースを明示的に有効にするには、 **[パブリッシャーのプロパティ - \<Publisher>]** ボックスの **[パブリケーション データベース]** ページを使用します。 このダイアログ ボックスへのアクセスの詳細については、「 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)」を参照してください。  
  
## <a name="using-sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS) の使用
  
1.  **[パブリッシャーのプロパティ - \<Publisher>]** ダイアログ ボックスの **[パブリケーション データベース]** ページで、レプリケートする各データベースの **[トランザクション]** チェック ボックスまたは **[マージ]** チェック ボックスをオンにします。 スナップショット レプリケーションのデータベースを有効にするには、 **[トランザクション]** を選択します。  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
  
## <a name="using-transact-sql-t-sql"></a>Transact-SQL (T-SQL) の使用
次の Transact-SQL コード を使用して、データベースのレプリケーションを有効にできます。 

```sql
USE master
EXEC sp_replicationdboption @dbname = 'AdventureWorks2017',
@optname = 'publish',
@value = 'true'
GO
```

パブリッシングを無効にするには、@value = 'false' を設定します。 
