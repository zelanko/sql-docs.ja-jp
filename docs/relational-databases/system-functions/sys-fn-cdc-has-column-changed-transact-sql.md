---
title: sys.fn_cdc_has_column_changed (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fn_cdc_has_column_changed_TSQL
- sys.fn_cdc_has_column_changed
- fn_cdc_has_column_changed_TSQL
- fn_cdc_has_column_changed
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fn_cdc_has_column_changed
- fn_cdc_has_column_changed
ms.assetid: 2b9e6278-050d-4ffc-8d1a-09606180facc
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 3d3df1bd07e73c3c363a0fd275e910c3c32cbe71
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47645180"
---
# <a name="sysfncdchascolumnchanged-transact-sql"></a>sys.fn_cdc_has_column_changed (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  特定の更新マスクと列を指定し、関連する変更行の特定の列が更新済みであるかどうかを判別します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.fn_cdc_has_column_changed ( 'capture_instance','column_name' , update_mask )  
```  
  
## <a name="arguments"></a>引数  
 **'** *capture_instance* **'**  
 キャプチャ インスタンスの名前を指定します。 *capture_instance*は**sysname**します。  
  
 **'** *column_name* **'**  
 指定したキャプチャ インスタンスのレポート対象となるキャプチャ対象列を指定します。 *column_name*は**sysname**します。  
  
 *update_mask*  
 関連する変更行の更新済み列を識別するマスクを指定します。 *update_mask*は**varbinary (128)** します。  
  
## <a name="return-type"></a>戻り値の型  
 **bit**  
  
## <a name="remarks"></a>コメント  
 この関数を使用すると、変更データ クエリで返された更新マスクから情報を抽出できます。 主に、更新マスクの後処理で、関連する変更行の特定の列が変更されているかどうかを知る必要がある場合などに使用します。 詳細については、「[変更データ キャプチャについて &#40;SQL Server&#41;](../../relational-databases/track-changes/about-change-data-capture-sql-server.md)」を参照してください。  
  
 関数を使用することをお勧めこの情報は、変更データ クエリの一部として返されます、 [sys.fn_cdc_get_column_ordinal](../../relational-databases/system-functions/sys-fn-cdc-get-column-ordinal-transact-sql.md)と[sys.fn_cdc_is_bit_set](../../relational-databases/system-functions/sys-fn-cdc-is-bit-set-transact-sql.md)この関数の代わりにします。 必要な列序数が 1 回しか計算されないようにするために、変更データを照会する前に fn_cdc_get_column_ordinal 関数を使用します。 クエリ内で fn_cdc_is_bit_set を使用して、返された各行の更新マスクから情報を抽出します。  
  
## <a name="permissions"></a>アクセス許可  
 固定サーバー ロール sysadmin または固定データベース ロール db_owner のメンバーシップが必要です。 それ以外のすべてのユーザーについては、ソース テーブルのすべてのキャプチャ対象列に対する SELECT 権限が必要です。さらに、キャプチャ インスタンスのゲーティング ロールが定義されている場合は、そのデータベース ロールのメンバーシップが必要です。  
  
## <a name="see-also"></a>参照  
 [cdc です。&#60;capture_instance&#62;_CT &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/cdc-capture-instance-ct-transact-sql.md)   
 [cdc.captured_columns &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/cdc-captured-columns-transact-sql.md)  
  
  
