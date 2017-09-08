---
title: "DBCC PDW_SHOWEXECUTIONPLAN (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.service: sql-data-warehouse
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
caps.latest.revision: 12
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 461ee87f41692172b31125e36553c0eab0b09772
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="dbcc-pdwshowexecutionplan-transact-sql"></a>DBCC PDW_SHOWEXECUTIONPLAN (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

表示、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]特定で実行されているクエリの実行プラン[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]ノードまたはノードのコントロールを計算します。 クエリの計算ノードと管理 ノードで実行中に、クエリ パフォーマンスの問題のトラブルシューティングを行うには、これを使用します。
  
SMP のクエリ パフォーマンスの問題が認識されたら[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンピューティング ノードで実行されているクエリはパフォーマンスを向上させるためにいくつかの方法があります。 複数列統計を作成する、非クラスター化インデックスを作成する、またはクエリ ヒントを使用してコンピューティング ノードでのクエリのパフォーマンスを向上させる方法が含まれます。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [TRANSACT-SQL 構文表記規則 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
SQL Server の構文:

```sql
DBCC PDW_SHOWEXECUTIONPLAN ( distribution_id, spid )  
[;]  
```  
Azure の並列データ ウェアハウスの構文:
  
```sql
DBCC PDW_SHOWEXECUTIONPLAN ( pdw_node_id, spid )  
[;]  
```  
  
## <a name="arguments"></a>引数  
 *distribution_id*  
 クエリ プランが実行されている分布の識別子。 これは、整数であり、NULL にすることはできません。 対象とする場合に使用される[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]です。  
  
 *pdw_node_id*  
 クエリ プランを実行しているノードの識別子です。 これは、整数であり、NULL にすることはできません。 アプライアンスを対象とする場合に使用します。  
  
 *spid*  
 識別子、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クエリ プランを実行しているセッションです。 これは、整数であり、NULL にすることはできません。  
  
## <a name="permissions"></a>Permissions  
 に対する CONTROL 権限が必要です[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]です。  
  
アプライアンス上の VIEW SERVER STATE 権限が必要です。
  
## <a name="examples-includesssdwincludessssdw-mdmd"></a>例:[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]  
  
### <a name="a-dbcc-pdwshowexecutionplan-basic-syntax"></a>A. DBCC PDW_SHOWEXECUTIONPLAN の基本的な構文  
 実行されているときに、[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]インスタンスのまた、distribution_id を選択する上記のクエリを変更します。  
  
```sql
SELECT [sql_spid], [pdw_node_id], [request_id], [dms_step_index], [type], [start_time], [end_time], [status], [distribution_id]  
FROM sys.dm_pdw_dms_workers   
WHERE [status] <> 'StepComplete' and [status] <> 'StepError'  
order by request_id, [dms_step_index];  
```  
  
これは、積極的に個々 の配布を実行するため、spid の値を返します。 どのような配布 1 が 375 のセッションで実行されていたか調べたい場合は、次のコマンドを実行はします。
  
```sql
DBCC PDW_SHOWEXECUTIONPLAN ( 1, 375 );  
```  

## <a name="examples-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
### <a name="b-dbcc-pdwshowexecutionplan-basic-syntax"></a>B. DBCC PDW_SHOWEXECUTIONPLAN の基本的な構文  
 長時間実行されているクエリは、DMS を実行するか、プランの操作またはクエリ プランの操作が SQL クエリを実行します。  
  
クエリでは、DM クエリ プランの操作を実行している場合、は、ノード Id と手順については、不完全なセッション Id の一覧を取得する次のクエリを使用することができます。
  
```sql
SELECT [sql_spid], [pdw_node_id], [request_id], [dms_step_index], [type], [start_time], [end_time], [status]   
FROM sys.dm_pdw_dms_workers   
WHERE [status] <> 'StepComplete' and [status] <> 'StepError'  
AND pdw_node_id = 201001   
order by request_id, [dms_step_index], [distribution_id];  
```  
  
上記のクエリの結果に基づき、DBCC PDW_SHOWEXEUCTIONPLAN へのパラメーターとして、sql_spid と pdw_node_id を使用します。 たとえば、次のコマンドでは、pdw_node_id 201001 と sql_spid 375 の実行プランが表示されます。
  
```sql
DBCC PDW_SHOWEXECUTIONPLAN ( 201001, 375 );  
```  

## <a name="see-also"></a>参照
[DBCC PDW_SHOWPARTITIONSTATS & #40 です。TRANSACT-SQL と #41 です。](dbcc-pdw-showpartitionstats-transact-sql.md)  
[DBCC PDW_SHOWSPACEUSED & #40 です。TRANSACT-SQL と #41 です。](dbcc-pdw-showspaceused-transact-sql.md)
