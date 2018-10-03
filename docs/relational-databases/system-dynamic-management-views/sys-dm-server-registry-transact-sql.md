---
title: sys.dm_server_registry (TRANSACT-SQL) |Microsoft Docs
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
manager: craigg
ms.openlocfilehash: e4e0b1069977c14216952e537d4bd12b28190529
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47788620"
---
# <a name="sysdmserverregistry-transact-sql"></a>sys.dm_server_registry (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の現在のインスタンスについて Windows レジストリに格納されている構成情報とインストール情報を返します。 レジストリ キーごとに 1 行を返します。 この動的管理ビューなどの情報を返すを使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスのホスト コンピューターまたはネットワーク構成の値で使用できるサービス[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|registry_key|**nvarchar (256)**|レジストリ キーの名前。 NULL 値が許可されます。|  
|value_name|**nvarchar (256)**|キー値の名前。 これに表示される項目、**名前**レジストリ エディターの列。 NULL 値が許可されます。|  
|value_data|**sql_variant**|キー データの値。 値は、これは、**データ**レジストリ エディター、指定されたエントリの列。 NULL 値が許可されます。|  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>アクセス許可  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-display-the-sql-server-services"></a>A. SQL Server サービスを表示します。  
 次の例では、SQL Server の現在のインスタンスについて SQL Server および SQL Server エージェント サービスのレジストリ キーの値を返します。  
  
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
WHERE registry_key = N'CurrentVersion';  
```  
  
### <a name="d-display-the-parameters-passed-to-the-instance-of-sql-server-during-startup"></a>D. スタートアップ中に SQL Server のインスタンスに渡されるパラメーターを表示します。  
 次の例では、スタートアップ中に SQL Server のインスタンスに渡されるパラメーターを返します。  
  
```  
SELECT registry_key, value_name, value_data  
FROM sys.dm_server_registry  
WHERE registry_key LIKE N'%Parameters';  
```  
  
### <a name="e-return-network-configuration-information-for-the-instance-of-sql-server"></a>E. SQL Server のインスタンスに関するネットワーク構成情報を返します。  
 次の例では、SQL Server の現在のインスタンスに関するネットワーク構成の値を返します。  
  
```  
SELECT registry_key, value_name, value_data  
FROM sys.dm_server_registry  
WHERE registry_key LIKE N'%SuperSocketNetLib%';  
```  
  
## <a name="see-also"></a>参照  
 [sys.dm_server_services &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-services-transact-sql.md)  
  
  
