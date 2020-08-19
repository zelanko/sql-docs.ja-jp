---
description: sysmail_help_profile_sp (Transact-SQL)
title: sysmail_help_profile_sp (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_help_profile_sp_TSQL
- sysmail_help_profile_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_help_profile_sp
ms.assetid: d7169a8e-92b1-49eb-9124-3b2f69755ddb
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 372f2309176b9fcf9cbb36fbcaf89d710393bb44
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88419296"
---
# <a name="sysmail_help_profile_sp-transact-sql"></a>sysmail_help_profile_sp (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  1 つ以上のメール プロファイルに関する情報を一覧表示します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sysmail_help_profile_sp  [   [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' ]  
```  
  
## <a name="arguments"></a>引数  
`[ @profile_id = ] profile_id` 情報を返すプロファイル id。 *profile_id* は **int**,、既定値は NULL です。  
  
`[ @profile_name = ] 'profile_name'` 情報を返すプロファイル名。 *profile_name* は **sysname**,、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 次の列を含む結果セットが返されます。  
  
| 列名 | データ型 | 説明 |
| ----------- | --------- | ----------- |
|**profile_id**|**int**|プロファイルのプロファイル id。|  
|**name**|**sysname**|プロファイルのプロファイル名。|  
|**description**|**nvarchar (256)**|プロファイルの説明。|  
  
## <a name="remarks"></a>解説  
 プロファイル名またはプロファイル id が指定されている場合、 **sysmail_help_profile_sp** はそのプロファイルに関する情報を返します。 それ以外の場合、 **sysmail_help_profile_sp** は、インスタンス内のすべてのプロファイルに関する情報を返し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
 ストアドプロシージャ **sysmail_help_profile_sp** は **msdb** データベースにあり、 **dbo** スキーマが所有しています。 現在のデータベースが **msdb**でない場合は、3つの部分で構成される名前を使用してプロシージャを実行する必要があります。  
  
## <a name="permissions"></a>アクセス許可  
 このプロシージャの実行権限は、既定では **sysadmin** 固定サーバーロールのメンバーに与えています。  
  
## <a name="examples"></a>例  
 **A. すべてのプロファイルを一覧表示する**  
  
 次の例では、インスタンス内のすべてのプロファイルを一覧表示します。  
  
```  
EXECUTE msdb.dbo.sysmail_help_profile_sp;  
```  
  
 次に示すのは、行の長さに対して再フォーマットされる、結果セットのサンプルです。  
  
```  
profile_id  name                          description  
----------- ----------------------------- ------------------------------  
56          AdventureWorks Administrator  Administrative mail profile.    
57          AdventureWorks Operator       Operator mail profile.          
```  
  
 **B. 特定のプロファイルを一覧表示する**  
  
 次の例では、プロファイル `AdventureWorks Administrator` に関する情報を一覧表示します。  
  
```  
EXECUTE msdb.dbo.sysmail_help_profile_sp  
    @profile_name = 'AdventureWorks Administrator' ;  
```  
  
 次に示すのは、行の長さに対して再フォーマットされる、結果セットのサンプルです。  
  
```  
profile_id  name                          description  
----------- ----------------------------- ------------------------------  
56          AdventureWorks Administrator  Administrative mail profile.    
```  
  
## <a name="see-also"></a>参照  
 [データベース メール](../../relational-databases/database-mail/database-mail.md)   
 [Transact-sql&#41;&#40;のストアドプロシージャのデータベースメール ](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
