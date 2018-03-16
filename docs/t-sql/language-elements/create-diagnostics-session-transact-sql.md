---
title: CREATE DIAGNOSTICS SESSION (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 662d019e-f217-49df-9e2f-b5662fa0342d
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: d869ed18b07f824ffa4cc3fc8b746ded5242ed99
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="create-diagnostics-session-transact-sql"></a>CREATE DIAGNOSTICS SESSION (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  診断セッションを使用すると、システムまたはクエリのパフォーマンスに詳細なユーザー定義の診断情報を保存することができます。  
  
 診断のセッションは通常、特定のクエリのパフォーマンスをデバッグする、またはアプライアンス操作中に特定のアプライアンス コンポーネントの動作を監視する場合に使用します。  
  
> [!NOTE]  
>  診断セッションを使用するために XML を熟知してください。  
  
## <a name="syntax"></a>構文  
  
```  
Creating a new diagnostics session:  
CREATE DIAGNOSTICS SESSION diagnostics_name AS N’{<session_xml>}’;  
  
<session_xml>::  
<Session>  
   [ <MaxItemCount>max_item_count_num</MaxItemCount> ]  
   <Filter>  
      { \<Event Name=”event_name”/>  
         [ <Where>\<filter_property_name Name=”value” ComparisonType="comp_type"/></Where> ] [ ,...n ]  
      } [ ,...n ]  
   </Filter> ]   
   <Capture>  
      \<Property Name=”property_name”/> [ ,...n ]  
   </Capture>  
<Session>  
  
Retrieving results for a diagnostics session:  
SELECT * FROM master.sysdiag.diagnostics_name ;  
  
Removing results for a diagnostics session:  
DROP DIAGNOSTICS SESSION diagnostics_name ;  
```  
  
## <a name="arguments"></a>引数  
 *diagnostics_name*  
 診断セッションの名前。 診断セッションの名前には、文字 a ～ z、A ～ Z、0 ～ 9 のみを含めることができます。 また、診断セッションの名前は、文字で開始する必要があります。 *diagnostics_name* の上限は 127 文字です。  
  
 *max_item_count_num*  
 ビューに保存されるイベントの数。 たとえば、100 を指定すると場合、は、フィルター条件に一致する最新の 100 のイベントを診断セッションを永続化は。 イベントの照合の 100 よりも少ないが見つかると、診断のセッションが 100 未満のイベントが含まれます。 *max_item_count_num* は 100 以上 100,000 以下である必要があります。  
  
 *event_name*  
 診断セッションで収集する実際のイベントを定義します。  *event_name* は、`sys.pdw_diag_events.is_enabled='True'` の場合に [sys.pdw_diag_events](http://msdn.microsoft.com/en-us/d813aac0-cea1-4f53-b8e8-d26824bc2587) に列挙されるイベントの 1 つです。  
  
 *filter_property_name*  
 結果を制限するプロパティの名前です。 たとえば、セッション ID に基づいて制限する場合は、*filter_property_name* を *SessionId* にする必要があります。 *filter_property_name* に使用できる値の一覧については、以下の *property_name* を参照してください。  
  
 *value*  
 *filter_property_name* に対して評価する値。 値の型は、プロパティの型と一致する必要があります。 たとえば、プロパティの型が decimal の場合、*value* の型も decimal である必要があります。  
  
 *comp_type*  
 比較型。 潜在的な値が: Equals、EqualsOrGreaterThan、EqualsOrLessThan、GreaterThan、LessThan、NotEquals、Contains、正規表現  
  
 *property_name*  
 イベントに関連するプロパティです。  プロパティの名前は、キャプチャのタグの一部を使用またはフィルターの条件の一部として使用します。  
  
|プロパティ名|Description|  
|-------------------|-----------------|  
|UserName|ユーザー (ログイン) の名前です。|  
|SessionId|セッション ID。|  
|QueryId|クエリの id。|  
|CommandType|コマンドの種類。|  
|CommandText|処理コマンドのテキストです。|  
|[OperationType]|イベントの操作の種類。|  
|Duration|イベントの期間です。|  
|SPID|サービスの プロセス id です。|  
  
## <a name="remarks"></a>Remarks  
 各ユーザーには、最大 10 個の同時実行の診断セッションに許可します。 現在のセッションの一覧については、[sys.pdw_diag_sessions](http://msdn.microsoft.com/en-us/ca111ddc-2787-4205-baf0-1a242c0257a9) を参照してください。不要なセッションがある場合は、`DROP DIAGNOSTICS SESSION` を使用して削除します。  
  
 診断セッションでは、収集のメタデータが削除されるまで続行されます。  
  
## <a name="permissions"></a>アクセス許可  
 **ALTER SERVER STATE** アクセス許可が必要です。  
  
## <a name="locking"></a>ロック  
 診断セッションの表に、上には、共有ロックを取得します。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-creating-a-diagnostics-session"></a>A. 診断セッションを作成します。  
 この例では、データベース エンジンのパフォーマンスのメトリックを記録する診断セッションを作成します。 この例では、エンジンのクエリの実行時刻から終了イベントと、ブロックの DMS イベントをリッスンする診断セッションを作成します。 返される結果は、コマンド テキスト、コンピューター名、要求 id (クエリの id)、イベントが作成されたセッションです。  
  
```  
CREATE DIAGNOSTICS SESSION MYDIAGSESSION AS N'  
<Session>  
   <MaxItemCount>100</MaxItemCount>  
   <Filter>  
      <Event Name="EngineInstrumentation:EngineQueryRunningEvent" />  
      <Event Name="DmsCoreInstrumentation:DmsBlockingQueueEnqueueBeginEvent" />  
      <Where>  
         <SessionId Value="381" ComparisonType="NotEquals" />  
      </Where>  
   </Filter>  
   <Capture>  
      <Property Name="Query.CommandText" />  
      <Property Name="MachineName" />  
      <Property Name="Query.QueryId" />  
      <Property Name="Alias" />  
      <Property Name="Duration" />  
      <Property Name="Session.SessionId" />  
   </Capture>  
</Session>';  
```  
  
 診断セッションの作成後に、クエリを実行します。  
  
```  
SELECT COUNT(EmployeeKey) FROM AdventureWorksPDW2012..FactSalesQuota;  
```  
  
 Sysdiag スキーマからを選択して、診断セッションの結果を表示します。  
  
```  
SELECT * FROM master.sysdiag.MYDIAGSESSION;  
```  
  
 Sysdiag スキーマには、診断セッションの名前、というビューが含まれていることを確認します。  
  
 接続のアクティビティのみを表示するには、`Session.SPID` プロパティを追加し、`WHERE [Session.SPID] = @@spid;` をクエリに追加します。  
  
 診断セッションが完了したら、**DROP DIAGNOSTICS** コマンドを使用して削除します。  
  
```  
DROP DIAGNOSTICS SESSION MYDIAGSESSION;  
```  
  
### <a name="b-alternative-diagnostic-session"></a>B. 別の診断セッション  
 わずかに異なるプロパティを持つ 2 番目の例です。  
  
```  
-- Determine the session_id of your current session  
SELECT TOP 1 session_id();  
-- Replace \<*session_number*> in the code below with the numbers in your session_id  
CREATE DIAGNOSTICS SESSION PdwOptimizationDiagnostics AS N'  
<Session>  
   <MaxItemCount>100</MaxItemCount>  
   <Filter>  
      <Event Name="EngineInstrumentation:MemoGenerationBeginEvent" />  
      <Event Name="EngineInstrumentation:MemoGenerationEndEvent" />  
      <Event Name="DSQLInstrumentation:OptimizationBeginEvent" />  
      <Event Name="DSQLInstrumentation:OptimizationEndEvent" />  
      <Event Name="DSQLInstrumentation:BuildRelOpContextTreeBeginEvent" />  
      <Event Name="DSQLInstrumentation:PostPlanGenModifiersEndEvent" />  
      <Where>  
         <SessionId Value="\<*session_number*>" ComparisonType="Equals" />  
      </Where>  
   </Filter>  
   <Capture>  
      <Property Name="Session.SessionId" />  
      <Property Name="Query.QueryId" />  
      <Property Name="Query.CommandText" />  
      <Property Name="Name" />  
      <Property Name="DateTimePublished" />  
      <Property Name="DateTimePublished.Ticks" />  
  </Capture>  
</Session>';  
```  
  
 など、クエリを実行します。  
  
```  
USE ssawPDW;  
GO  
SELECT * FROM dbo.FactFinance;  
```  
  
 次のクエリでは、承認のタイミングが返されます。  
  
```  
SELECT *   
FROM master.sysdiag.PdwOptimizationDiagnostics   
ORDER BY DateTimePublished;  
```  
  
 診断セッションが完了したら、**DROP DIAGNOSTICS** コマンドを使用して削除します。  
  
```  
DROP DIAGNOSTICS SESSION PdwOptimizationDiagnostics;  
```  
  
  
