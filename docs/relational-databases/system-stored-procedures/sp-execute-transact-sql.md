---
title: sp_execute (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cursor_execute
- sp_cursor_execute_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_execute
ms.assetid: 2009acd3-0d92-435a-a8fb-057e50dc7146
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ae3f46d5856aa061bac0dd06fb954052923a4d7d
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82827794"
---
# <a name="sp_execute-transact-sql"></a>sp_execute (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  [!INCLUDE[tsql](../../includes/tsql-md.md)]指定したハンドルと省略可能なパラメーター値を使用して、準備されたステートメントを実行します。 sp_execute は、ID = 12 を指定した場合に表形式のデータストリーム (TDS) パケットで呼び出されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
sp_execute handle OUTPUT  
    [,bound_param  ]  [,...n ]  ]  
```  
  
## <a name="arguments"></a>引数  
 *扱え*  
 Sp_prepare によって返される*ハンドル*値です。 *handle*は、 **int**入力値を呼び出す必須のパラメーターです。  
  
 *bound_param*  
 追加のパラメーターを使用することを示します。 *bound_param*は、プロシージャの追加パラメーターを示すために、任意のデータ型の入力値を呼び出す必須のパラメーターです。  
  
> [!NOTE]  
>  *bound_param*は、sp_prepare*params*値によって行われた宣言と一致する必要があり、 * @name = value*または*value*の形式で指定できます。  
  
## <a name="see-also"></a>参照  
 [システムストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sp_prepare &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-prepare-transact-sql.md)  
  
  
