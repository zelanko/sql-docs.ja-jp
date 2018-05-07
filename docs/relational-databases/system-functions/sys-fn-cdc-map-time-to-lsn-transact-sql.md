---
title: sys.fn_cdc_map_time_to_lsn (TRANSACT-SQL) |Microsoft ドキュメント
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
- sys.fn_cdc_map_time_to_lsn
- fn_cdc_map_time_to_lsn_TSQL
- sys.fn_cdc_map_time_to_lsn_TSQL
- fn_cdc_map_time_to_lsn
dev_langs:
- TSQL
helpviewer_keywords:
- fn_cdc_map_time_to_lsn
- sys.fn_cdc_map_time_to_lsn
ms.assetid: 6feb051d-77ae-4c93-818a-849fe518d1d4
caps.latest.revision: 23
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 32a4273a161e8b4cb443cdfa1601ad1bf419f426
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sysfncdcmaptimetolsn-transact-sql"></a>sys.fn_cdc_map_time_to_lsn (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ログ シーケンス番号 (LSN) の値を返します、 **start_lsn**内の列、 [cdc.lsn_time_mapping](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md)システム テーブルの指定した時刻。 この関数を使用するには、変更データ キャプチャの列挙関数に必要な LSN ベースの範囲に日付時刻範囲を体系的にマップする[cdc.fn_cdc_get_all_changes_ < capture_instance >](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md)と[cdc.fn_cdc_get_net_changes_ < capture_instance >](../../relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql.md)その範囲内のデータ変更を取得します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.fn_cdc_map_time_to_lsn ( '<relational_operator>', tracking_time )  
  
<relational_operator> ::=  
{  largest less than  
 | largest less than or equal  
 | smallest greater than  
 | smallest greater than or equal  
}  
```  
  
## <a name="arguments"></a>引数  
 **'**< relational_operator >**'** {よりも少ない最大 | よりも少ない最も大きいまたは等しい | 最小値を超える | 最小値より大きいか等しい}  
 内の個別の LSN 値を識別するため、 **cdc.lsn_time_mapping**テーブルが関連付け**tran_end_time**と比較したときに関係を満たす、 *tracking_time*値。  
  
 *relational_operator*は**nvarchar (30)** です。  
  
 *tracking_time*  
 照合する日付時刻値を指定します。 *tracking_time*は**datetime**です。  
  
## <a name="return-type"></a>戻り値の型  
 **binary(10)**  
  
## <a name="remarks"></a>解説  
 理解する方法、 **sys.fn_cdc_map_time_lsn**にマップする日付時刻範囲を LSN 範囲に、次のシナリオを検討してください。 使用することができます。 変更データを毎日抽出するとします。 つまり、特定の日の午前 0 時までに発生した変更を取得する必要があります。 時間範囲の下限は、前日の任意の時刻です (午前 0 時は含みません)。 上限は、特定の日の任意の時刻です (午前 0 時を含みます)。 例を次にどのように関数**sys.fn_cdc_map_time_to_lsn**をすべて返す変更データ キャプチャの列挙関数に必要な LSN ベースの範囲に、この時間ベースの範囲を体系的にマップするために使用します。その範囲内で変更します。  
  
 `DECLARE @begin_time datetime, @end_time datetime, @begin_lsn binary(10), @end_lsn binary(10);`  
  
 `SET @begin_time = '2007-01-01 12:00:00.000';`  
  
 `SET @end_time = '2007-01-02 12:00:00.000';`  
  
 `SELECT @begin_lsn = sys.fn_cdc_map_time_to_lsn('smallest greater than', @begin_time);`  
  
 `SELECT @end_lsn = sys.fn_cdc_map_time_to_lsn('largest less than or equal', @end_time);`  
  
 `SELECT * FROM cdc.fn_cdc_get_net_changes_HR_Department(@begin_lsn, @end_lsn, 'all` `');`  
  
 関係演算子 '`smallest greater than`' 前日の午前 0 時以降後に発生したものに変更を制限するために使用します。 複数のエントリでさまざまな LSN 値を共有する場合、 **tran_end_time**内の下限として識別される値、 [cdc.lsn_time_mapping](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md)テーブル、関数はことを確認する最小の LSN を返しますすべてのエントリが含まれます。 上限、関係演算子の '`largest less than or equal to`' 範囲にはとして午前 0 時よりも含め、その日のすべてのエントリが含まれていることを確認するために使用、 **tran_end_time**値。 複数のエントリでさまざまな LSN 値を共有する場合、 **tran_end_time**上限関数として識別される値はすべてのエントリが含まれる最大の LSN を返します。  
  
## <a name="permissions"></a>権限  
 ロール **public** のメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、`sys.fn_cdc_map_time_lsn`内の行があるかどうかを判断する関数、 [cdc.lsn_time_mapping](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md)を持つテーブル、 **tran_end_time**午前 0 時以上である値。 このクエリを使用すると、たとえば前日の午前 0 時を超えてコミットされた変更がキャプチャ プロセスによって既に処理されているかどうかに基づいてこの日の変更データの抽出を続行するかどうかを判定できます。  
  
```  
DECLARE @extraction_time datetime, @lsn binary(10);  
SET @extraction_time = '2007-01-01 12:00:00.000';  
SELECT @lsn = sys.fn_cdc_map_time_to_lsn ('smallest greater than or equal', @extraction_time);  
IF @lsn IS NOT NULL  
BEGIN  
<some action>  
END  
```  
  
## <a name="see-also"></a>参照  
 [cdc.lsn_time_mapping &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md)   
 [sys.fn_cdc_map_lsn_to_time &#40;TRANSACT-SQL&#41;](../../relational-databases/system-functions/sys-fn-cdc-map-lsn-to-time-transact-sql.md)   
 [cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;TRANSACT-SQL&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql.md)   
 [cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62;  &#40;TRANSACT-SQL&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md)  
  
  
