---
title: "sys.dm_clr_appdomains (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_clr_appdomains
- sys.dm_clr_appdomains
- dm_clr_appdomains_TSQL
- sys.dm_clr_appdomains_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_clr_appdomains dynamic management dynamic management view
ms.assetid: 9fe0d4fd-950a-4274-a493-85e776278045
caps.latest.revision: "24"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3dfe70d96c7b85d596c3819273acf264ba59e34b
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="sysdmclrappdomains-transact-sql"></a>sys.dm_clr_appdomains (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サーバー内のアプリケーション ドメインごとに 1 行のデータを返します。 アプリケーション ドメイン (**AppDomain**) 内の構造では、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]アプリケーションの分離の単位である共通言語ランタイム (CLR)。 このビューを使用するには理解やトラブルシューティングで実行されている CLR 統合オブジェクトに[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
 CLR 統合マネージ データベース オブジェクトにはいくつかの種類があります。 これらのオブジェクトについての概要については、次を参照してください。[共通言語ランタイム (CLR) 統合によるデータベース オブジェクトの構築](../../relational-databases/clr-integration/database-objects/building-database-objects-with-common-language-runtime-clr-integration.md)です。 これらのオブジェクトが実行されるたびに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を作成、 **AppDomain**が読み込むでき、必要なコードを実行します。 分離レベル、 **AppDomain**は 1 つ**AppDomain**所有者データベースごとにします。 つまり、ユーザーが所有するすべての CLR オブジェクトは、同じ実行常に**AppDomain**ごとのデータベース (場合、ユーザーが登録する CLR データベース オブジェクトで異なるデータベース、CLR データベース オブジェクトが異なるアプリケーション ドメインで実行されます)。 **AppDomain**コード実行の終了後は破棄されません。 代わりに、以降の実行に備えて、メモリ内にキャッシュされます。 これにより、パフォーマンスが向上します。  
  
 詳細については、次を参照してください。[アプリケーション ドメイン](http://go.microsoft.com/fwlink/p/?LinkId=299658)です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**appdomain_address**|**varbinary (8)**|アドレス、 **AppDomain**です。 ユーザーが所有するオブジェクトが同じで読み込まれた常にすべてのマネージ データベース**AppDomain**です。 この列を使用するにはこれで現在読み込まれているすべてのアセンブリを検索する**AppDomain**で**sys.dm_clr_loaded_assemblies**です。|  
|**appdomain_id**|**int**|ID、 **AppDomain**です。 各**AppDomain**が一意の id。|  
|**appdomain_name**|**varchar(386)**|名前、 **AppDomain**によって割り当てられた[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。|  
|**creation_time**|**datetime**|時刻、 **AppDomain**作成されました。 **AppDomains**はキャッシュされ、パフォーマンスを向上させるには、再使用**creation_time**必ずしもコードが実行された時間ではありません。|  
|**db_id**|**int**|このデータベースの ID **AppDomain**作成されました。 2 つの異なるデータベースに格納されているコードは、1 つを共有できません**AppDomain**です。|  
|**user_id**|**int**|これで実行できるオブジェクトを持つユーザーの ID **AppDomain**です。|  
|**状態**|**nvarchar (128)**|現在の状態の記述子、 **AppDomain**です。 AppDomain には作成から削除まで、さまざまな状態があります。 詳細については、このトピックの「解説」を参照してください。|  
|**strong_refcount**|**int**|強参照数**AppDomain**です。 これは、現在これを使用するバッチの実行の数を反映して**AppDomain**です。 このビューの実行を作成することに注意してください、**強力な参照カウント**以外の場合でも、現在実行されてコードがない**strong_refcount** 1 の値になります。|  
|**weak_refcount**|**int**|弱参照数**AppDomain**です。 これは、内部オブジェクトの数を示します、 **AppDomain**キャッシュされます。 マネージ データベース オブジェクトを実行するときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]キャッシュ内で、 **AppDomain**後で再使用します。 これにより、パフォーマンスが向上します。|  
|**コスト**|**int**|コスト、 **AppDomain**です。 コストが高いほど、この**AppDomain**がメモリ不足でアンロードされます。 通常、コストはメモリの量がこれを再作成するために必要な異なります**AppDomain**です。|  
|**値**|**int**|値、 **AppDomain**です。 値が低いほど、可能性が高くなりますこの**AppDomain**がメモリ不足でアンロードされます。 値は通常の接続またはバッチの数を使用しているこの異なります**AppDomain**です。|  
|**total_processor_time_ms**|**bigint**|プロセスの開始後、現在のアプリケーション ドメインでの実行中にすべてのスレッドによって使用された、ミリ秒単位の合計プロセッサ時間です。 これに相当**System.AppDomain.MonitoringTotalProcessorTime**です。|  
|**total_allocated_memory_kb**|**bigint**|アプリケーション ドメインの作成後、それによって行われたすべてのメモリ割り当ての、KB 単位の合計サイズです。収集されたメモリ量も差し引かれません。 これに相当**System.AppDomain.MonitoringTotalAllocatedMemorySize**です。|  
|**survived_memory_kb**|**bigint**|最後の完全なブロッキング コレクションで残った、現在のアプリケーション ドメインによって参照されていることが判明しているキロバイト数です。 これに相当**System.AppDomain.MonitoringSurvivedMemorySize**です。|  
  
## <a name="remarks"></a>解説  
 リレーションシップがある 1 つである間**dm_clr_appdomains.appdomain_address**と**dm_clr_loaded_assemblies.appdomain_address**です。  
  
 次の表の一覧の考えられる**状態**値とその説明で発生したときと、 **AppDomain**ライフ サイクルです。 ライフ サイクルを次にこの情報を使用することができます、 **AppDomain**疑わしいまたは繰り返し発生を監視する**AppDomain**インスタンスがアンロード中で、Windows イベント ログを解析する必要はありません。  
  
## <a name="appdomain-initialization"></a>AppDomain の初期化  
  
|状態|Description|  
|-----------|-----------------|  
|E_APPDOMAIN_CREATING|**AppDomain**作成中です。|  
  
## <a name="appdomain-usage"></a>AppDomain の使用状況  
  
|状態|Description|  
|-----------|-----------------|  
|E_APPDOMAIN_SHARED|ランタイム**AppDomain**が複数のユーザーが使用できる状態です。|  
|E_APPDOMAIN_SINGLEUSER|**AppDomain** DDL 操作で使用できる状態です。 これらは E_APPDOMAIN_SHARED とは異なり、CLR 統合の実行に DDL 操作ではなく共有 AppDomain が使用されます。 このような AppDomain は他の同時実行操作から分離されます。|  
|E_APPDOMAIN_DOOMED|**AppDomain** 、アンロードするようにスケジュールが現在稼働中のスレッドがある場合。|  
  
## <a name="appdomain-cleanup"></a>AppDomain のクリーンアップ  
  
|状態|Description|  
|-----------|-----------------|  
|E_APPDOMAIN_UNLOADING|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]CLR がアンロードする要求が、 **AppDomain**普通、マネージ データベース オブジェクトを含むアセンブリが変更または削除されたため、します。|  
|E_APPDOMAIN_UNLOADED|CLR がアンロードした、 **AppDomain**です。 これは、によるエスカレーション プロシージャの結果では通常**ThreadAbort**、 **OutOfMemory**、またはユーザー コードで未処理の例外。|  
|E_APPDOMAIN_ENQUEUE_DESTROY|**AppDomain**が CLR でアンロードおよび設定を破棄する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。|  
|E_APPDOMAIN_DESTROY|**AppDomain**によって破棄されているが[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。|  
|E_APPDOMAIN_ZOMBIE|**AppDomain**によって破棄された[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 ただし、すべてのを参照、 **AppDomain**クリーンアップされています。|  
  
## <a name="permissions"></a>Permissions  
 データベースに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例の詳細を表示する方法を示しています、 **AppDomain**特定のアセンブリ。  
  
```  
select appdomain_id, creation_time, db_id, user_id, state  
from sys.dm_clr_appdomains a  
where appdomain_address =   
(select appdomain_address   
 from sys.dm_clr_loaded_assemblies  
   where assembly_id = 500);  
```  
  
 次の例のすべてのアセンブリを表示する方法を示しています、指定された**AppDomain**:  
  
```  
select a.name, a.assembly_id, a.permission_set_desc, a.is_visible, a.create_date, l.load_time   
from sys.dm_clr_loaded_assemblies as l   
inner join sys.assemblies as a  
on l.assembly_id = a.assembly_id  
where l.appdomain_address =   
(select appdomain_address   
from sys.dm_clr_appdomains  
where appdomain_id = 15);  
```  
  
## <a name="see-also"></a>参照  
 [sys.dm_clr_loaded_assemblies &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-clr-loaded-assemblies-transact-sql.md)   
 [共通言語ランタイム関連の動的管理ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/common-language-runtime-related-dynamic-management-views-transact-sql.md)  
  
  
