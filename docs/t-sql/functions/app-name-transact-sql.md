---
title: APP_NAME (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- APP_NAME_TSQL
- APP_NAME
dev_langs:
- TSQL
helpviewer_keywords:
- name checking for current session [SQL Server]
- sessions [SQL Server], application names
- applications [SQL Server], names
- current session application names
- APP_NAME function
ms.assetid: e491e192-9b30-4243-bc19-33c133fe08a8
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: b2b65f2380cc52c7a1d084dedad5fdb744d377bf
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="appname-transact-sql"></a>APP_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

現在のセッションがアプリケーションによって設定されている場合、そのアプリケーションの名前を返します。
  
> [!IMPORTANT]  
>  まったく確認されていないアプリケーション名がクライアントから提供されました。 使用しない APP_NAME** セキュリティ チェックの一部として。  
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
  
APP_NAME  ( )  
```  
  
## <a name="return-types"></a>戻り値の型  
**nvarchar(128)**
  
## <a name="remarks"></a>Remarks  
使用して APP_NAME** の異なるアプリケーションのさまざまな操作を実行する場合。 たとえば、それぞれのアプリケーションに対して日付を異なる形式で指定したり、特定のアプリケーションに情報メッセージを返したりする場合などです。
  
アプリケーション名を設定する場合、[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] では、[データベース エンジンへの接続] **ダイアログ ボックスで、[オプション]** をクリックします。 **[追加の接続パラメーター]** タブ上で、**app** 属性を `;app='application_name'` 形式で指定します。
  
## <a name="examples"></a>使用例  
次の例では、このプロセスを開始したクライアント アプリケーションが `SQL Server Management Studio` セッションかどうかを確認し、日付を US または ANSI のいずれかの形式で指定します。
  
```sql
USE AdventureWorks2012;  
GO  
IF APP_NAME() = 'Microsoft SQL Server Management Studio - Query'  
PRINT 'This process was started by ' + APP_NAME() + '. The date is ' + CONVERT ( varchar(100) , GETDATE(), 101) + '.';  
ELSE   
PRINT 'This process was started by ' + APP_NAME() + '. The date is ' + CONVERT ( varchar(100) , GETDATE(), 102) + '.';  
GO  
```  
  
## <a name="see-also"></a>参照
[システム関数 &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)  
[関数](../../t-sql/functions/functions.md)
  
  
