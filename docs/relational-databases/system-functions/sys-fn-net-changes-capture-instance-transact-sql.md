---
title: sys.fn_net_changes_&lt;capture_instance&gt; (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server (starting with 2008)
f1_keywords:
- sys.fn_net_changes_TSQL
- fn_net_changes_TSQL
- fn_net_changes
- sys.fn_net_changes
dev_langs:
- TSQL
helpviewer_keywords:
- fn_net_changes_<capture_instance>
- sys.fn_net_changes_<capture_instance>
ms.assetid: 342fa030-9fd9-4b74-ae4d-49f6038a5073
caps.latest.revision: 16
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: e787c487e2fb03619346de73234427c3499ef5f4
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/16/2018
ms.locfileid: "40393518"
---
# <a name="sysfnnetchangesltcaptureinstancegt-transact-sql"></a>sys.fn_net_changes_&lt;capture_instance&gt; (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  用のラッパー、**変更の net**関数をクエリします。 これらの関数を作成するために必要なスクリプトは、sys.sp_cdc_generate_wrapper_function ストアド プロシージャで生成されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
fn_net_changes_<capture_instance> ('start_time', 'end_time', '<row_filter_option>' )  
  
<capture_instance> ::= The name of the capture instance.  
<row_filter_option> ::=  
{ all  
  | all with mask  
  | all with merge  
}  
```  
  
## <a name="arguments"></a>引数  
 *start_time*  
 **Datetime**を結果セットに含める変更テーブル エントリの範囲の下端を表す値です。  
  
 Cdc. < capture_instance > _CT 内の行をより厳密に大きい関連するコミット時間を持つテーブルの変更のみ*start_time*結果セットに含まれます。  
  
 この引数に NULL 値を指定した場合、クエリ範囲の下限は、キャプチャ インスタンスの有効な範囲の下限に対応します。  
  
 *end_time*  
 **Datetime**を結果セットに含める変更テーブル エントリの範囲の上端を表す値です。  
  
 に対して選択した値に応じて、2 つの意味のいずれかでこのパラメーターを取ることができます@closed_high_end_pointラッパー関数を作成するスクリプトを生成する sys.sp_cdc_generate_wrapper_function を呼び出すときに。  
  
-   @closed_high_end_point = 1  
  
     Cdc. < capture_instance > _CT 内の行で値があるテーブルの変更のみ\_ \_$start_lsn 列および対応するコミット時間に等しいまたはそれよりも小さい**start_time**結果セットに含まれます。  
  
-   @closed_high_end_point = 0  
  
     Cdc. < capture_instance > _CT 内の行で値があるテーブルの変更のみ\_ \_$start_lsn 列および対応するコミット時間より小さい**start_time**結果セットに含まれます。  
  
 この引数に NULL 値を指定した場合、クエリ範囲の上限は、キャプチャ インスタンスの有効な範囲の上限に対応します。  
  
 *< row_filter_option >* :: = {すべて | マスク | すべてのマージで}  
 結果セットで返される行と同様に、メタデータ列の内容を制御するオプション。 次のいずれかのオプションを指定できます。  
  
 all  
 変更された行の最終的な内容がコンテンツ列に返され、その行を適用するために必要な操作がメタデータ列 __CDC_OPERATION に返されます。  
  
 all with mask  
 変更されたすべての行の最終的な内容がコンテンツ列に返され、その各行を適用するために必要な操作がメタデータ列 __CDC_OPERATION に返されます。 ラッパー関数の作成スクリプトの生成時に更新フラグの一覧を指定した場合、このオプションを使用して更新マスクを設定する必要があります。  
  
 all with merge  
 変更されたすべての行の最終的な内容がコンテンツ列に返されます。  
  
 __CDC_OPERATION 列の値は、次の 2 つのいずれかになります。  
  
-   行を削除する必要がある場合は D  
  
-   行を挿入または更新する必要がある場合は M  
  
 変更を適用するために挿入と更新のどちらが必要であるかを特定するロジックでは、クエリが複雑になってしまいます。 挿入操作と更新操作を区別する必要がない場合は、パフォーマンスを向上させるためにこのオプションを使用してください。 このアプローチは、マージ操作が、直接などに使用できるターゲット環境で最適な[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]環境。  
  
## <a name="table-returned"></a>返されるテーブル  
  
|列名|列の型|説明|  
|-----------------|-----------------|-----------------|  
|\<列から@column_list>|**varies**|指定されている列、 **column_list**引数のために sp_cdc_generate_wrapper_function 際が呼び出され、ラッパーを作成するスクリプトを生成します。 場合*column_list* NULL の場合は、すべての追跡対象ソース列が結果セットに表示されます。|  
|__CDC_OPERATION|**nvarchar(2)**|ターゲット環境に行を適用するために必要な操作を表す操作コードです。 操作の引数の値は異なります*row_filter_option*は、次の呼び出しで渡されます。<br /><br /> *row_filter_option* = 'all'、'all with mask'<br /><br /> 'D' : 削除操作<br /><br /> 'I' : 挿入操作<br /><br /> 'UN' : 更新操作<br /><br /> *row_filter_option* = 'all with merge'<br /><br /> 'D' : 削除操作<br /><br /> 'M' : 挿入操作または更新操作|  
|\<列から@update_flag_list>|**bit**|列名の後に "_uflag" が付加されている、ビット フラグです。 フラグが null 以外の値が場合にのみ*row_filter_option* **= 'all with mask'** と\__CDC_OPERATION **= 'UN'** します。 対応する列がクエリ ウィンドウ内で変更された場合は、1 に設定されます。 それ以外の場合は、0 に設定されます。|  
  
## <a name="remarks"></a>コメント  
 fn_net_changes_<capture_instance> 関数は、cdc.fn_cdc_get_net_changes_<capture_instance> クエリ関数のラッパーとして機能します。 ラッパーのスクリプトを作成するには、sys.sp_cdc_generate_wrapper ストアド プロシージャを使用します。  
  
 ラッパー関数が自動的に作成されることはありません。 ラッパー関数を作成するには、次の 2 つを行う必要があります。  
  
1.  ラッパーの作成スクリプトを生成するストアド プロシージャを実行します。  
  
2.  スクリプトを実行して、実際にラッパー関数を作成します。  
  
 ラッパー関数は、体系的にクエリで範囲指定された期間内に発生する変更点についてユーザーを有効にする**datetime** LSN 値での値の代わりにします。 ラッパー関数が提供されている間、すべての必要な変換を実行**datetime**値およびクエリ関数の引数として内部的に必要な LSN 値です。 データが紛失または繰り返し、次の規則に準拠していることを確認しますが、ラッパー関数は変更データのストリームを処理する順番に使用する場合: @end_time として1回の呼び出しに関連付けられている間隔の値が指定されました。@start_time後続の呼び出しに関連付けられている間隔の値。  
  
 使用して、@closed_high_end_pointパラメーター、スクリプトを作成するときに、指定のクエリ ウィンドウで、閉じた上限または開いている上限のいずれかをサポートするラッパーを生成することができます。 つまり、抽出期間の上限とコミット時間が等しいエントリを、その期間に含めるかどうかを決定できます。 既定では、上限が含まれます。  
  
 によって返される結果セットは、**変更の net**ラッパー関数は、追跡対象列に含まれていたのみを返し、@column_listラッパーが生成されたとき。 場合@column_listが null の場合、すべての追跡対象ソース列が返されます。 ソース列に続いて、操作列 __CDC_OPERATION が返されます。これは、操作を表す 1 文字か 2 文字の列です。  
  
 ビット フラグがパラメーターで指定されている各列の結果セットに追加し、@update_flag_listします。 **変更の net**あれば、ビット フラグは常に NULL にする場合、@row_filter_optionは 'all' または 'all with merge' は、ラッパー関数の呼び出しで使用します。 場合、 @row_filter_option 'all with mask'、かつ _ _cdc_operation に設定されている必要があるが ' または 'I'、フラグの値は NULL にもなります。 場合\__CDC_OPERATION が ' UN '、1 または 0 かどうかに応じて、フラグが設定されます、 **net**列への変更の原因となった操作を更新します。  
  
 変更データ キャプチャの構成テンプレート "Instantiate CDC Wrapper TVFs for Schema" には、sp_cdc_generate_wrapper_function ストアド プロシージャを使用して、スキーマの定義済みクエリ関数に対するすべてのラッパー関数の CREATE スクリプトを取得する方法が示されています。 このテンプレートで、それらのスクリプトが作成されます。 テンプレートの詳細については、次を参照してください。[テンプレート エクスプ ローラー](../../ssms/template/template-explorer.md)します。  
  
## <a name="see-also"></a>参照  
 [sys.sp_cdc_generate_wrapper_function &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-generate-wrapper-function-transact-sql.md)   
 [cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;TRANSACT-SQL&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql.md)  
  
  
