---
title: データベース マスター キーの作成 | Microsoft Docs
ms.custom: ''
ms.date: 01/02/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- database master key [SQL Server], creating
ms.assetid: 8cb24263-e97d-4e4d-9429-6cf494a4d5eb
author: aliceku
ms.author: aliceku
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f3034dc76a64e25b614b1871247369214199c36b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62521275"
---
# <a name="create-a-database-master-key"></a>データベース マスター キーの作成
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用してデータベース マスター キーを作成する方法について説明します。
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>アクセス許可  
データベースに対する CONTROL 権限が必要です。  
  
## <a name="using-transact-sql"></a>Transact-SQL の使用  
  
### <a name="to-create-a-database-master-key"></a>データベース マスター キーを作成するには  
  
1. データベースに格納するマスター キーのコピーを暗号化するためのパスワードを指定します。  
  
2. **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。  
  
3. [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
4. 次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
    ```sql
    -- Creates a database master key for the "AdventureWorks2012" database.   
    -- The key is encrypted using the password "23987hxJ#KL95234nl0zBe."  
    USE AdventureWorks2012;  
    GO  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '23987hxJ#KL95234nl0zBe';  
    GO  
    ```  
  
 詳細については、[CREATE MASTER KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/create-master-key-transact-sql.md)を参照してください。  
