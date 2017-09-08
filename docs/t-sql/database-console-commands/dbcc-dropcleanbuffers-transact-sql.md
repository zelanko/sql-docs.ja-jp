---
title: "DBCC DROPCLEANBUFFERS (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROPCLEANBUFFERS
- DBCC_DROPCLEANBUFFERS_TSQL
- DROPCLEANBUFFERS_TSQL
- DBCC DROPCLEANBUFFERS
dev_langs:
- TSQL
helpviewer_keywords:
- clean buffers
- cold buffer cache
- buffer pools [SQL Server]
- dropping buffers
- removing buffers
- DBCC DROPCLEANBUFFERS statement
ms.assetid: a4121927-f2ce-4926-aa2c-9b1519dac048
caps.latest.revision: 35
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d1a7a1507e230995df1c2b67a8499a12270b535c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="dbcc-dropcleanbuffers-transact-sql"></a>DBCC DROPCLEANBUFFERS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

バッファー プール、および columnstore オブジェクト プールからの列ストア オブジェクトからすべてのクリーン バッファーを削除します。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文
SQL Server の構文: 

```sql
DBCC DROPCLEANBUFFERS [ WITH NO_INFOMSGS ]  
```  
Azure SQL ウェアハウスと並列データ ウェアハウスの構文:

```sql  
DBCC DROPCLEANBUFFERS ( COMPUTE | ALL ) [ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>引数  
 WITH NO_INFOMSGS  
 すべての情報メッセージを表示しないようにします。 情報メッセージがで抑制常に[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]です。  
  
 COMPUTE  
 すべての計算ノードには、クエリ プランのキャッシュを削除します。  
  
 ALL  
 各計算ノードおよび [管理] ノードからは、クエリ プランのキャッシュを消去します。 これは、値を指定しない場合の既定値です。  
  
## <a name="remarks"></a>解説  
サーバーのシャットダウンと再起動を行わずに、コールド バッファー キャッシュの状態でクエリをテストする場合は、DBCC DROPCLEANBUFFERS を使用します。
Columnstore オブジェクト プールからバッファー プールと列ストア オブジェクトからクリーン バッファーを削除、コールド バッファー キャッシュを生成するために最初のチェックポイントを使用します。 これで、現在のデータベースのすべてのダーティ ページがディスクに書き込まれ、バッファーが削除されます。 その後、DBCC DROPCLEANBUFFERS コマンドを実行してバッファー プールからバッファーを削除します。
  
## <a name="result-sets"></a>結果セット  
DBCC DROPCLEANBUFFERS[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を返します。
  
```sql
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
  
## <a name="permissions"></a>Permissions  

適用されます SQL Server、並列データ ウェアハウス。 

- **sysadmin** 固定サーバー ロールのメンバーシップが必要です。  

適用対象: Azure SQL Data Warehouse

- DB_OWNER 固定サーバー ロールのメンバーシップが必要です。  
  
## <a name="see-also"></a>参照  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[CHECKPOINT &#40;Transact-SQL&#41;](../../t-sql/language-elements/checkpoint-transact-sql.md)  
  
  

