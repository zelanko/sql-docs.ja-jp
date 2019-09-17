---
title: データベース マスター キーの作成 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2019
ms.prod: sql-server-2014
ms.reviewer: carlrab
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- database master key [SQL Server], creating
ms.assetid: 8cb24263-e97d-4e4d-9429-6cf494a4d5eb
author: aliceku
ms.author: aliceku
manager: craigg
ms.openlocfilehash: 757b6c62d63da2b8f1fa33e5d704d7a2c4fabd38
ms.sourcegitcommit: 5a61854ddcd2c61bb6da30ccad68f0ad90da0c96
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2019
ms.locfileid: "70978367"
---
# <a name="create-a-database-master-key"></a>データベース マスター キーの作成

このトピックでは、で`master` [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]を使用[!INCLUDE[tsql](../../../includes/tsql-md.md)]して、データベースにデータベースマスターキーを作成する方法について説明します。

**このトピックの内容**

- **作業を開始する準備:**

  [Security](#Security)

- [Transact-SQL を使用してデータベース マスター キーを作成するには](#TsqlProcedure)

## <a name="BeforeYouBegin"></a> はじめに

### <a name="Security"></a> セキュリティ

#### <a name="Permissions"></a> Permissions

データベースに対する CONTROL 権限が必要です。

## <a name="TsqlProcedure"></a> Transact-SQL の使用

### <a name="to-create-a-database-master-key"></a>データベース マスター キーを作成するには

1. データベースに格納するマスター キーのコピーを暗号化するためのパスワードを指定します。
2. **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。
3. **[システムデータベース]** を展開し`master` 、を右クリックして、 **[新しいクエリ]** をクリックします。
4. 次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。

  ```sql
  -- Creates the master key.
  -- The key is encrypted using the password "23987hxJ#KL95234nl0zBe."
  CREATE MASTER KEY ENCRYPTION BY PASSWORD = '23987hxJ#KL95234nl0zBe';
```

詳細については、[CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql)を参照してください。
