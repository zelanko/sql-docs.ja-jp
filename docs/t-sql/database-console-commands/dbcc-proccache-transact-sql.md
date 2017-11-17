---
title: "DBCC PROCCACHE (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|database-console-commands
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DBCC PROCCACHE
- DBCC_PROCCACHE_TSQL
- PROCCACHE_TSQL
- PROCCACHE
dev_langs:
- TSQL
helpviewer_keywords:
- procedure cache [SQL Server]
- displaying procedure cache information
- DBCC PROCCACHE statement
ms.assetid: 7a4f9f8a-13ff-4bf2-ba29-c17012a23659
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 97e617e7867c90bf1e66c5e64e37b9039087d463
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="dbcc-proccache-transact-sql"></a>DBCC PROCCACHE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

テーブル フォーマット内のプロシージャ キャッシュに関する情報を表示します。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
DBCC PROCCACHE [ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>引数  
 のすべてのメンションを  
 オプションを指定できます。  
  
 NO_INFOMSGS  
 重大度レベル 0 ～ 10 のすべての情報メッセージを表示しないようにします。  
  
## <a name="remarks"></a>解説  
プロシージャ キャッシュを使用してコンパイル済みの実行プランをキャッシュし、バッチの実行速度を上げます。 プロシージャ キャッシュ内のエントリはバッチ レベルです。 プロシージャ キャッシュには、次のエントリが含まれます。
-   コンパイル済みプラン  
-   実行プラン  
-   代数ツリー  
-   拡張プロシージャ  
  
## <a name="result-sets"></a>結果セット  
次の表では、結果セットの列について説明します。
  
|列名|Description|  
|-----------------|-----------------|  
|**num proc マニア**|プロシージャ キャッシュ内のすべてのエントリで使用されるページの総数です。|  
|**num proc マニアの使用**|現在使用されているすべてのエントリで使用されるページの総数です。|  
|**アクティブな num proc マニア**|これは旧バージョンとの互換性のためにだけ用意されています。 現在使用されているすべてのエントリで使用されるページの総数です。|  
|**プロシージャ キャッシュのサイズ**|プロシージャ キャッシュ内のエントリの総数です。|  
|**プロシージャ キャッシュの使用**|現在使用されているエントリの総数です。|  
|**プロシージャ キャッシュがアクティブです**|これは旧バージョンとの互換性のためにだけ用意されています。 現在使用されているエントリの総数です。|  
  
## <a name="permissions"></a>Permissions  
**sysadmin** 固定サーバー ロールまたは **db_owner** 固定データベース ロールのメンバーシップが必要です。
  
## <a name="see-also"></a>参照  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)
  
  

