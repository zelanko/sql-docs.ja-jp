---
title: "APP_NAME (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
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
caps.latest.revision: 35
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c4f63ae216bad0269415ac5e0aa57a7543500f0c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="appname-transact-sql"></a>APP_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

現在のセッションがアプリケーションによって設定されている場合、そのアプリケーションの名前を返します。
  
> [!IMPORTANT]  
>  まったく確認されていないアプリケーション名がクライアントから提供されました。 使用しないでください**APP_NAME**セキュリティ チェックの一部として。  
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
  
APP_NAME  ( )  
```  
  
## <a name="return-types"></a>戻り値の型  
**nvarchar (128)**
  
## <a name="remarks"></a>解説  
使用して**APP_NAME**異なるアプリケーションに対して異なるアクションを実行する場合。 たとえば、それぞれのアプリケーションに対して日付を異なる形式で指定したり、特定のアプリケーションに情報メッセージを返したりする場合などです。
  
アプリケーション名を設定する[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]で、**データベース エンジンへの接続**ダイアログ ボックスで、をクリックして**オプション**です。 **追加の接続パラメーター**  タブで、提供、**アプリ**形式で属性`;app='application_name'`
  
## <a name="examples"></a>使用例  
次の例は、このプロセスを開始したクライアント アプリケーションではあるかどうかを確認、`SQL Server Management Studio`セッションし、US または ANSI のいずれかの形式で日付を提供します。
  
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
[システム関数 & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/system-functions-for-transact-sql.md)  
[関数](../../t-sql/functions/functions.md)
  
  

