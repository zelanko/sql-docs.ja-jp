---
title: sp_prepare (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 02/28/2018
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_cursor_prepare_TSQL
- sp_cursor_prepare
dev_langs:
- TSQL
helpviewer_keywords:
- sp_prepare
ms.assetid: f328c9eb-8211-4863-bafa-347e1bf7bb3f
caps.latest.revision: 9
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 896894b05823cdfeaa1efa3cda7c341a7fa9f010
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39535352"
---
# <a name="spprepare-transact-sql"></a>sp_prepare (Transact SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  パラメーター化された準備[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントとステートメントを返します*処理*実行します。 sp_prepare は、ID を指定して呼び出される、表形式データ ストリーム (TDS) パケットで 11 を = です。  
  
 ![記事リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_prepare handle OUTPUT, params, stmt, options  
```  
  
## <a name="arguments"></a>引数  
 *handle*  
 SQL Server によって生成される*準備済みハンドル*識別子。 *処理*必須のパラメーターには、 **int**値を返します。  
  
 *params*  
 パラメーター化されたステートメントを指定します。 *Params*変数の定義は、ステートメント内のパラメーター マーカーの代わりに使用します。 *params*が必要なパラメーターです、 **ntext**、 **nchar**、または**nvarchar**値を入力します。 ステートメントがパラメーター化されていない場合は、NULL 値を入力します。  
  
 *stmt*  
 カーソル結果セットを定義します。 *Stmt*パラメーターは必須でありの呼び出し、 **ntext**、 **nchar**、または**nvarchar**値を入力します。  
  
 *options*  
 カーソル結果セット列の説明を返す省略可能なパラメーターです。 *オプション*int の次の入力値が必要です。  
  
|値|説明|  
|-----------|-----------------|  
|0x0001|RETURN_METADATA|  
  
## <a name="examples"></a>使用例  
 次の例では、単純なステートメントを準備して実行します。  
  
```  
Declare @P1 int;  
Exec sp_prepare @P1 output,   
    N'@P1 nvarchar(128), @P2 nvarchar(100)',  
    N'SELECT database_id, name FROM sys.databases WHERE name=@P1 AND state_desc = @P2';  
Exec sp_execute @P1, N'tempdb', N'ONLINE';  
EXEC sp_unprepare @P1;  
```  

  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

