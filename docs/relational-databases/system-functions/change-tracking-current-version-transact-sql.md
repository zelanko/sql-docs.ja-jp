---
title: CHANGE_TRACKING_CURRENT_VERSION (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 08/08/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- CHANGE_TRACKING_CURRENT_VERSION_TSQL
- CHANGE_TRACKING_CURRENT_VERSION
dev_langs:
- TSQL
helpviewer_keywords:
- change tracking [SQL Server], CHANGE_TRACKING_CURRENT_VERSION
- CHANGE_TRACKING_CURRENT_VERSION
ms.assetid: 3027c4f7-6b4d-4089-a369-5926e8a8da1c
author: rothja
ms.author: jroth
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e1bf8d568031541df8f4dfa80a4148ad759dad54
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68042997"
---
# <a name="change_tracking_current_version-transact-sql"></a>CHANGE_TRACKING_CURRENT_VERSION (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  最後にコミットされたトランザクションに関連付けられているバージョンを返します。 このバージョンは、 [CHANGETABLE](../../relational-databases/system-functions/changetable-transact-sql.md)を使用して変更を列挙するときに使用できます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
CHANGE_TRACKING_CURRENT_VERSION ( )  
```  
  
## <a name="return-type"></a>戻り値の型  
 **bigint**  
  
## <a name="remarks"></a>Remarks  
 データベースで変更の追跡が有効になっていない場合に、NULL を返します。  
  
## <a name="examples"></a>使用例  
 次の例では、追跡された変更の現在のバージョンを格納するローカル変数 `@next_baseline` を宣言し、`CHANGE_TRACKING_CURRENT_VERSION()` 関数を使用してこの変数の値を取得します。  
  
```sql  
DECLARE @next_baseline bigint;  
SET @next_baseline = CHANGE_TRACKING_CURRENT_VERSION();  
```  
  
## <a name="see-also"></a>参照  
 [Change Tracking 関数 &#40;Transact-sql&#41;](../../relational-databases/system-functions/change-tracking-functions-transact-sql.md)   
 [CHANGETABLE &#40;Transact-sql&#41;](../../relational-databases/system-functions/changetable-transact-sql.md)   
 [CHANGE_TRACKING_MIN_VALID_VERSION &#40;Transact-sql&#41;](../../relational-databases/system-functions/change-tracking-min-valid-version-transact-sql.md)   
 [データ変更の追跡 &#40;SQL Server&#41;](../../relational-databases/track-changes/track-data-changes-sql-server.md)  
  
  
