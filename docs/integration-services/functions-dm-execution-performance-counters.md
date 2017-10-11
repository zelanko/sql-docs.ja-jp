---
title: "dm_execution_performance_counters (SSISDB データベース) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 1b38e8e3-c560-4b6e-b60e-bfd7cfcd4fdf
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 67d5ece89f5b964acb2bb55a8cc69ff2fb77b93b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="functions---dmexecutionperformancecounters"></a>機能 - dm_execution_performance_counters
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サーバーで処理中の実行のパフォーマンス統計を返します。  
  
## <a name="syntax"></a>構文  
  
```sql  
dm_execution_performance_counters [ @execution_id = ] execution_id  
  
```  
  
## <a name="arguments"></a>引数  
 [ @execution_id =] *execution_id*  
 1 つまたは複数のパッケージを含む実行の一意識別子。 パッケージ実行タスクで実行されるパッケージは、親パッケージと同じ実行で実行されます。  
  
 実行 ID が指定されていない場合は、複数の実行のパフォーマンス統計が返されます。 メンバーである場合、 **ssis_admin** データベース ロール、実行中のすべての実行のパフォーマンス統計が返されます。  メンバーでない場合、 **ssis_admin** データベース ロール、実行中に、アクセス許可を参照する実行のパフォーマンス統計が返されます。 *Execution_id*は、 **BigInt**です。  
  
## <a name="remarks"></a>解説  
 次の表に、dm_execution_performance_counter 関数によって返されるカウンター名の値を一覧で示します。  
  
|カウンター名|Description|  
|------------------|-----------------|  
|BLOB bytes read|データ フロー エンジンがすべてのソースから読み取るバイナリ ラージ オブジェクト (BLOB) データのバイト数。|  
|BLOB bytes written|データ フロー エンジンがすべての出力先に書き込む BLOB データのバイト数。|  
|BLOB files in use|データ フロー エンジンがスプールのために使用している BLOB ファイル数。|  
|Buffer memory|物理メモリや仮想メモリなど、Integration Services のバッファーによって使用されるメモリ量。|  
|Buffers in use|すべてのデータ フロー コンポーネントおよびデータ フロー エンジンが使用している、すべての種類のバッファー オブジェクト数。|  
|Buffers Spooled|ディスクに書き込むバッファーの数。|  
|Flat buffer memory|すべてのフラット バッファーが使用するメモリ量 (バイト単位)。 フラット バッファーはコンポーネントがデータの格納に使用するメモリ ブロックです。|  
|Flat buffers in use|データ フロー エンジンが使用するフラット バッファー数。 フラット バッファーはすべてプライベート バッファーです。|  
|Private buffer memory|すべてのプライベート バッファーが使用しているメモリ量。 プライベート バッファーは、変換が一時作業のために使用するバッファーです。<br /><br /> データ フロー エンジンがデータ フローをサポートするためにバッファーを作成する場合、バッファーはプライベートではありません。|  
|Private buffers in use|変換が一時作業のために使用するバッファー数。|  
|Rows read|実行準備ができている行の合計数。|  
|Rows written|実行によって書き込まれた行の合計数。|  
  
## <a name="return"></a>戻り値  
 dm_execution_performance_counters 関数は、1 つの処理中の実行に対して次の列を持つ表を返します。 返す情報は、実行に含まれているすべてのパッケージが対象です。 処理中の実行がない場合は、空の表を返します。  
  
|列名|列の型|Description|解説|  
|-----------------|-----------------|-----------------|-------------|  
|execution_id|**Bigint 型**<br /><br /> **NULL**は有効な値ではありません。|パッケージを含む実行の一意識別子。||  
|counter_name|**nvarchar (128)**|カウンターの名前。|参照してください、**解説**値のセクションでします。|  
|counter_value|**Bigint 型**|カウンターによって返される値です。||  
  
## <a name="example"></a>例  
 次の例では、ID が 34 である処理中の実行の統計を関数で返します。  
  
```sql
select * from [catalog].[dm_execution_performance_counters] (34)  
```  
  
## <a name="example"></a>例  
 次の例では、関数で実行されているすべての実行の統計を返します。、[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]権限に応じて、サーバーです。  
  
```sql
select * from [catalog].[dm_execution_performance_counters] (NULL)  
  
```  
  
## <a name="permissions"></a>Permissions  
 この関数には、次の権限のいずれかが必要です。  
  
-   実行のインスタンスの READ および MODIFY 権限  
  
-   メンバーシップを**ssis_admin**データベース ロール  
  
-   メンバーシップを**sysadmin**サーバーの役割  
  
## <a name="errors-and-warnings"></a>エラーおよび警告  
 関数が失敗する原因となる条件を以下に示します。  
  
-   ユーザーには指定された実行に対する MODIFY 権限がない。  
  
-   指定された実行 ID が無効である。  
  
  
