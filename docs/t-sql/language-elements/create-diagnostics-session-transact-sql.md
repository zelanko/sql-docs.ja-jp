---
title: "診断セッション (TRANSACT-SQL) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 662d019e-f217-49df-9e2f-b5662fa0342d
caps.latest.revision: 9
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 71f3463ad4d91bd117c322e9e63c0b331b07ca9f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-diagnostics-session-transact-sql"></a>診断セッション (TRANSACT-SQL) を作成します。
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw_md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

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
 診断セッションの名前。 診断セッションの名前には、文字 a ～ z、A ～ Z、0 ～ 9 のみを含めることができます。 また、診断セッションの名前は、文字で開始する必要があります。 *diagnostics_name*は 127 文字に制限されます。  
  
 *max_item_count_num*  
 ビューに保存されるイベントの数。 たとえば、100 を指定すると場合、は、フィルター条件に一致する最新の 100 のイベントを診断セッションを永続化は。 イベントの照合の 100 よりも少ないが見つかると、診断のセッションが 100 未満のイベントが含まれます。 *max_item_count_num* 100 以上にする必要があります 100,000 以下です。  
  
 *event_name*  
 診断セッションで収集する実際のイベントを定義します。  *event_name*で示されているイベントの 1 つ[sys.pdw_diag_events](http://msdn.microsoft.com/en-us/d813aac0-cea1-4f53-b8e8-d26824bc2587)場所`sys.pdw_diag_events.is_enabled='True'`です。  
  
 *filter_property_name*  
 結果を制限するプロパティの名前です。 たとえば、セッション id に基づいたを制限する*filter_property_name*する必要があります*SessionId*です。 参照してください*property_name*の下の潜在的な値の一覧については*filter_property_name*です。  
  
 *value*  
 値に対して評価する*filter_property_name*です。 値の型は、プロパティの型と一致する必要があります。 たとえば、次のプロパティの型が 10 進数の型*値*10 進数である必要があります。  
  
 *comp_type*  
 比較の種類。 潜在的な値が: Equals、EqualsOrGreaterThan、EqualsOrLessThan、GreaterThan、LessThan、NotEquals、Contains、正規表現  
  
 *property_name*  
 イベントに関連するプロパティです。  プロパティの名前は、キャプチャのタグの一部を使用またはフィルターの条件の一部として使用します。  
  
|プロパティ名|Description|  
|-------------------|-----------------|  
|UserName|ユーザー (ログイン) の名前です。|  
|SessionId|セッション id です。|  
|QueryId|クエリの id。|  
|CommandType|コマンドの種類。|  
|CommandText|処理コマンドのテキストです。|  
|[OperationType]|イベントの操作の種類。|  
|Duration|イベントの期間です。|  
|SPID|サービスの プロセス id です。|  
  
## <a name="remarks"></a>解説  
 各ユーザーには、最大 10 個の同時実行の診断セッションに許可します。 参照してください[sys.pdw_diag_sessions](http://msdn.microsoft.com/en-us/ca111ddc-2787-4205-baf0-1a242c0257a9)の現在のセッション、および drop のいずれかを使用してセッションが不要な一覧については`DROP DIAGNOSTICS SESSION`します。  
  
 診断セッションでは、収集のメタデータが削除されるまで続行されます。  
  
## <a name="permissions"></a>Permissions  
 必要があります、 **ALTER SERVER STATE**権限です。  
  
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
  
 接続のアクティビティのみを表示するには、追加、`Session.SPID`プロパティを追加および`WHERE [Session.SPID] = @@spid;`クエリにします。  
  
 診断セッションが終了したら、ドロップを使用して、**ドロップ診断**コマンド。  
  
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
  
 診断セッションが終了したら、ドロップを使用して、**ドロップ診断**コマンド。  
  
```  
DROP DIAGNOSTICS SESSION PdwOptimizationDiagnostics;  
```  
  
  
