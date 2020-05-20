---
title: データベース マスター キーの作成 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2019
ms.prod: sql-server-2014
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- database master key [SQL Server], creating
ms.assetid: 8cb24263-e97d-4e4d-9429-6cf494a4d5eb
author: jaszymas
ms.author: jaszymas
manager: craigg
ms.reviewer: carlrab
ms.openlocfilehash: cc0b3e0dccd1ecf674d583e4d1b7adc1a85341d2
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82758888"
---
# <a name="create-a-database-master-key"></a>データベース マスター キーの作成

このトピックでは、でを使用して、データベースにデータベースマスターキーを作成する方法について説明し `master` [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] [!INCLUDE[tsql](../../../includes/tsql-md.md)] ます。

**このトピックの内容**

- **作業を開始する準備:**

  [Security](#Security)

- [Transact-SQL を使用してデータベース マスター キーを作成するには](#TsqlProcedure)

## <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに

### <a name="security"></a><a name="Security"></a> セキュリティ

#### <a name="permissions"></a><a name="Permissions"></a> Permissions

データベースに対する CONTROL 権限が必要です。

## <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Transact-SQL の使用

### <a name="to-create-a-database-master-key"></a>データベース マスター キーを作成するには

1. データベースに格納するマスター キーのコピーを暗号化するためのパスワードを指定します。
2. **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。
3. **[システム データベース]** を展開し、`master` を右クリックして、**[新しいクエリ]** をクリックします。
4. 次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。

  ```sql
  -- Creates the master key.
  -- The key is encrypted using the password "23987hxJ#KL95234nl0zBe."
  CREATE MASTER KEY ENCRYPTION BY PASSWORD = '23987hxJ#KL95234nl0zBe';
```

詳細については、[CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql)を参照してください。
