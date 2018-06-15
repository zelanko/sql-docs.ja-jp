---
title: sys.fn_all_changes_&lt;capture_instance&gt; (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/02/2016
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
- fn_all_changes
- sys.fn_all_changes
- fn_all_changes_TSQL
- sys.fn_all_changes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- fn_all_changes_<capture_instance>
- sys.fn_all_changes_<capture_instance>
ms.assetid: 564fae96-b88c-4f22-9338-26ec168ba6f5
caps.latest.revision: 15
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: ad305781c542be9bee59eb0dce6328df8a6f603a
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33238812"
---
# <a name="sysfnallchangesltcaptureinstancegt-transact-sql"></a>sys.fn_all_changes_&lt;capture_instance&gt; (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ラッパー、**すべての変更**関数をクエリします。 これらの関数を作成するために必要なスクリプトは、sys.sp_cdc_generate_wrapper_function ストアド プロシージャで生成されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
fn_all_changes_<capture_instance> ('start_time' ,'end_time', '<row_filter_option>' )  
  
<capture_instance> ::= The name of the capture instance.  
<row_filter_option> ::=  
{ all  
  | all update old  
}  
```  
  
## <a name="arguments"></a>引数  
 *start_time*  
 **Datetime**を結果セットに含める変更テーブル エントリの範囲の下端を表す値です。  
  
 Cdc. < capture_instance > _CT 内の行を関連するコミット時間よりも大きい値を持つテーブルの変更のみ*start_time*結果セットに含まれます。  
  
 この引数に NULL 値を指定した場合、クエリ範囲の下限は、キャプチャ インスタンスの有効な範囲の下限に対応します。  
  
 *end_time*  
 **Datetime**を結果セットに含める変更テーブル エントリの範囲の上端を表す値です。  
  
 に対して選択した値に応じて 2 つの可能性のある意味のいずれかでこのパラメーターを取る@closed_high_end_pointラッパー関数の作成スクリプトを生成する sys.sp_cdc_generate_wrapper_function が呼び出されたとき。  
  
-   @closed_high_end_point = 1  
  
     結果セットには、cdc.<capture_instance>_CT 変更テーブル内の行のうち、関連するコミット時間が end_time 以前の行だけが格納されます。  
  
-   @closed_high_end_point = 0  
  
     結果セットには、cdc.capture_instance_CT 変更テーブル内の行のうち、関連するコミット時間が end_time より前の行だけが格納されます。  
  
 この引数に NULL 値を指定した場合、クエリ範囲の上限は、キャプチャ インスタンスの有効な範囲の上限に対応します。  
  
 <row_filter_option> ::= { all | all update old }  
 結果セットとして返される行およびメタデータ列の内容を制御するオプションです。  
  
 次のいずれかのオプションを指定できます。  
  
 all  
 指定された LSN 範囲内のすべての変更を返します。 更新操作により発生した変更の場合は、このオプションは、更新プログラムが適用された後に、新しい値を含む行のみを返します。  
  
 all update old  
 指定された LSN 範囲内のすべての変更を返します。 更新操作で生じた変更の場合、更新前と更新後の列値を格納した行が返されます。  
  
## <a name="table-returned"></a>返されるテーブル  
  
|列名|列の型|Description|  
|-----------------|-----------------|-----------------|  
|__CDC_STARTLSN|**binary(10)**|変更に関連付けられているトランザクションのコミット LSN です。 同じトランザクションでコミットされたすべての変更は、同じコミット LSN を共有します。|  
|__CDC_SEQVAL|**binary(10)**|特定のトランザクションに含まれる行の変更を並べ替えるためのシーケンス値です。|  
|\<列@column_list>|**varies**|指定されている列、 *column_list*ラッパー関数を作成するスクリプトを生成することが呼び出されるとため sp_cdc_generate_wrapper_function 際に渡す引数。|  
|__CDC_OPERATION|**nvarchar(2)**|ターゲット環境に行を適用するための操作を表す操作コードです。 引数の値に基づいてが異なります*row_filter_option*呼び出し時に指定します。<br /><br /> *row_filter_option* = 'all'<br /><br /> 'D' : 削除操作<br /><br /> 'I' : 挿入操作<br /><br /> 'UN' : 新しい値の更新操作<br /><br /> *row_filter_option* 'all は update old' を =<br /><br /> 'D' : 削除操作<br /><br /> 'I' : 挿入操作<br /><br /> 'UN' : 新しい値の更新操作<br /><br /> 'UO' : 古い値の更新操作|  
|\<列@update_flag_list>|**bit**|ビット フラグの名前は、列の名前を _uflag を付加しました。 フラグは常に場合、NULL に設定\__CDC_OPERATION が、'、'I'、または 'UO' のです。 ときに\__CDC_OPERATION が ' UN '、更新によって対応する列が変更される場合に 1 に設定されています。 それ以外の場合は、0 に設定されます。|  
  
## <a name="remarks"></a>解説  
 fn_all_changes_<capture_instance> 関数は、cdc.fn_cdc_get_all_changes_<capture_instance> クエリ関数のラッパーとして機能します。 ラッパーを作成するスクリプトを生成するには、sys.sp_cdc_generate_wrapper ストアド プロシージャを使用します。  
  
 ラッパー関数が自動的に作成されることはありません。 ラッパー関数を作成するには、次の 2 つを行う必要があります。  
  
1.  ラッパーの作成スクリプトを生成するストアド プロシージャを実行します。  
  
2.  スクリプトを実行して、実際にラッパー関数を作成します。  
  
 ラッパー関数は、体系的にクエリで範囲指定期間内に発生する変更についてユーザーを有効にする**datetime** LSN 値での値の代わりにします。 ラッパー関数が提供されている間、すべての必要な変換を実行**datetime**値と、クエリ関数の引数として内部的に必要な LSN 値です。 データはありませんが欠落や重複の次の規則に従ったことが支えますとき、ラッパー関数は、変更データのストリームを処理する順番に使用して、: @end_time として1回の呼び出しに関連付けられている間隔の値が指定されました。@start_time後続の呼び出しに関連付けられている間隔の値。  
  
 使用して、@closed_high_end_pointパラメーター、スクリプトを作成するときに、指定したクエリ ウィンドウで、閉じた上限または開いた上限をサポートするラッパーを生成できます。 つまり、抽出期間の上限とコミット時間が等しいエントリを、その期間に含めるかどうかを決定できます。 既定では、上限が含まれます。  
  
 によって返される結果セットは、**すべての変更**ラッパー関数を返します、_ _ $start_lsn と\_ \_$seqval 列を変更テーブルの列として\__CDC_STARTLSN と\__CDC_SEQVAL、それぞれします。 これらに表示されていた追跡対象列のみを次に、 *@column_list*ラッパー生成時のパラメーターです。 場合*@column_list*が NULL の場合、すべての追跡対象ソース列が返されます。 ソース列には、操作列が続く\__CDC_OPERATION、これは、操作を識別する 1 つまたは 2 文字列です。  
  
 次に、@update_flag_list パラメーターで指定された各列の結果セットに対し、ビット フラグが追加されます。 **すべての変更**ラッパー、ビット フラグは常に NULL になります _ _cdc_operation がある場合は '、'I' または 'UO' です。 場合\__CDC_OPERATION が ' UN '、1 または 0 の場合、更新操作が列に変更を発生させたかどうかに応じて、フラグが設定されます。  
  
 変更データ キャプチャの構成テンプレート "Instantiate CDC Wrapper TVFs for Schema" には、sp_cdc_generate_wrapper_function ストアド プロシージャを使用して、スキーマの定義済みクエリ関数に対するすべてのラッパー関数の CREATE スクリプトを取得する方法が示されています。 このテンプレートで、それらのスクリプトが作成されます。 テンプレートの詳細については、次を参照してください。[テンプレート エクスプ ローラー](http://msdn.microsoft.com/library/b9ee55c5-bb44-4f76-90ac-792d8d83b4c8)です。  
  
## <a name="see-also"></a>参照  
 [sys.sp_cdc_generate_wrapper_function &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-generate-wrapper-function-transact-sql.md)   
 [cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62;  &#40;TRANSACT-SQL&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md)  
  
  
