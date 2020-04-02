---
title: dm_server_registry (トランザクション-SQL) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_server_registry_TSQL
- sys.dm_server_registry
- dm_server_registry
- sys.dm_server_registry_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_server_registry dynamic management view
ms.assetid: 9b3e0c74-2e99-4996-a383-104d51831e97
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8daa2d195ab1f4cf4602b9633394ed1705a3d7d2
ms.sourcegitcommit: 1124b91a3b1a3d30424ae0fec04cfaa4b1f361b6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2020
ms.locfileid: "80530823"
---
# <a name="sysdm_server_registry-transact-sql"></a>dm_server_registry (トランザクション-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の現在のインスタンスについて Windows レジストリに格納されている構成情報とインストール情報を返します。 レジストリ キーごとに 1 行を返します。 この動的管理ビューを使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ホスト マシンで使用可能なサービスや、 の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスのネットワーク構成値などの情報を返します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|registry_key|**nvarchar(256)**|レジストリ キー名。 NULL 値が許可されます。|  
|value_name|**nvarchar(256)**|キー値の名前。 これは、レジストリ エディタの **[名前]** 列に表示される項目です。 NULL 値が許可されます。|  
|value_data|**Sql_variant**|キー データの値。 これは、特定のエントリのレジストリ エディターの **[データ**] 列に表示される値です。 NULL 値が許可されます。|  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>アクセス許可  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-display-the-sql-server-services"></a>A. SQL Server サービスを表示する  
 次の例では、SQL Server の現在のインスタンスの SQL Server および SQL Server エージェント サービスのレジストリ キー値を返します。  
  
```  
SELECT registry_key, value_name, value_data  
FROM sys.dm_server_registry  
WHERE registry_key LIKE N'%ControlSet%';  
```  
  
### <a name="b-display-the-sql-server-agent-registry-key-values"></a>B. SQL Server エージェントのレジストリ キーの値を表示します。  
 次の例では、SQL Server の現在のインスタンスについて SQL Server エージェントのレジストリ キーの値を返します。  
  
```  
SELECT registry_key, value_name, value_data  
FROM sys.dm_server_registry  
WHERE registry_key LIKE N'%SQLAgent%';  
```  
  
### <a name="c-display-the-current-version-of-the-instance-of-sql-server"></a>C. SQL Server のインスタンスの現在のバージョンを表示します。  
 次の例では、SQL Server の現在のインスタンスのバージョンを返します。  
  
```  
SELECT registry_key, value_name, value_data  
FROM sys.dm_server_registry  
WHERE value_name = N'CurrentVersion';  
```  
  
### <a name="d-display-the-parameters-passed-to-the-instance-of-sql-server-during-startup"></a>D. スタートアップ中に SQL Server のインスタンスに渡されるパラメーターを表示します。  
 次の例では、スタートアップ中に SQL Server のインスタンスに渡されるパラメーターを返します。  
  
```  
SELECT registry_key, value_name, value_data  
FROM sys.dm_server_registry  
WHERE registry_key LIKE N'%Parameters';  
```  
  
### <a name="e-return-network-configuration-information-for-the-instance-of-sql-server"></a>E. SQL Server のインスタンスのネットワーク構成情報を返す  
 次の例では、SQL Server の現在のインスタンスに関するネットワーク構成の値を返します。  
  
```  
SELECT registry_key, value_name, value_data  
FROM sys.dm_server_registry  
WHERE registry_key LIKE N'%SuperSocketNetLib%';  
```  
  
## <a name="see-also"></a>参照  
 [トランザクションSQL&#41;&#40;sys.dm_server_services](../../relational-databases/system-dynamic-management-views/sys-dm-server-services-transact-sql.md)  
  
  
