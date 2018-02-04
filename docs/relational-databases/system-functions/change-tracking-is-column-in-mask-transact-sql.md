---
title: "CHANGE_TRACKING_IS_COLUMN_IN_MASK (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/08/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CHANGE_TRACKING_IS_COLUMN_IN_MASK_TSQL
- CHANGE_TRACKING_IS_COLUMN_IN_MASK
dev_langs:
- TSQL
helpviewer_keywords:
- change tracking [SQL Server], CHANGE_TRACKING_IS_COLUMN_IN_MASK
- CHANGE_TRACKING_IS_COLUMN_IN_MASK
ms.assetid: 649b370b-da54-4915-919d-1b597a39d505
caps.latest.revision: 
author: BYHAM
ms.author: rickbyh
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 88deb96a5f27568b8cfcfa3fc7ddcc6d43019d76
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="changetrackingiscolumninmask-transact-sql"></a>CHANGE_TRACKING_IS_COLUMN_IN_MASK (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  CHANGETABLE(CHANGES ...) 関数によって返される SYS_CHANGE_COLUMNS 値を解釈します。 これにより、指定した列が SYS_CHANGE_COLUMNS に返された値に含まれているかどうかを、アプリケーションで判断することができます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
CHANGE_TRACKING_IS_COLUMN_IN_MASK ( column_id , change_columns )  
```  
  
## <a name="arguments"></a>引数  
 *column_id*  
 チェックする列の ID です。 使用して ID を取得できる列、 [COLUMNPROPERTY](../../t-sql/functions/columnproperty-transact-sql.md)関数。  
  
 *change_columns*  
 バイナリ データの SYS_CHANGE_COLUMNS 列から、 [CHANGETABLE](../../relational-databases/system-functions/changetable-transact-sql.md)データ。  
  
## <a name="return-type"></a>戻り値の型  
 **bit**  
  
## <a name="return-values"></a>戻り値  
 CHANGE_TRACKING_IS_COLUMN_IN_MASK は次の値を返します。  
  
|戻り値|Description|  
|------------------|-----------------|  
|0|指定した列がない、 *change_columns*  ボックスの一覧です。|  
|1|指定された列は、 *change_columns*  ボックスの一覧です。|  
  
## <a name="remarks"></a>解説  
 CHANGE_TRACKING_IS_COLUMN_IN_MASK を検証するには、どのチェックは行われず、 *column_id*値、すなわち、 *change_columns*パラメーターは、元のテーブルから取得された、 *column_id*取得されました。  
  
## <a name="examples"></a>使用例  
 次の例を決定するかどうか、`Salary`の列、`Employees`テーブルが更新されました。 `COLUMNPROPERTY`関数、列の ID を返します、`Salary`列です。 `@change_columns` CHANGETABLE をデータ ソースとして使用して、クエリの結果をローカル変数を設定する必要があります。  
  
```sql  
SET @SalaryChanged = CHANGE_TRACKING_IS_COLUMN_IN_MASK  
    (COLUMNPROPERTY(OBJECT_ID('Employees'), 'Salary', 'ColumnId')  
    ,@change_columns);  
```  
  
## <a name="see-also"></a>参照  
 [変更追跡関数 &#40;Transact-SQL&#41;](../../relational-databases/system-functions/change-tracking-functions-transact-sql.md)   
 [CHANGETABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/changetable-transact-sql.md)   
 [データ変更の追跡 &#40;SQL Server&#41;](../../relational-databases/track-changes/track-data-changes-sql-server.md)  
  
  
