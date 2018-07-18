---
title: sys.dm_db_xtp_merge_requests (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 02/01/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: table-view-index
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c1224e88-af74-4c99-ae32-d5d2c552a1f5
caps.latest.revision: 2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 262fb2743efef806c31cf1b452a214150691e255
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38048520"
---
# <a name="sysdmdbxtpmergerequests-transact-sql"></a>sys.dm_db_xtp_merge_requests (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]


データベースのマージ要求を追跡します。 マージ要求が SQL Server によって生成されたかを持つユーザーによって要求が行われる可能性がありますが[sys.sp_xtp_merge_checkpoint_files (TRANSACT-SQL)](../../relational-databases/system-stored-procedures/sys-sp-xtp-merge-checkpoint-files-transact-sql.md)します。

> [!NOTE]
> この動的管理ビュー (DMV)、Microsoft SQL Server 2014 まで sys.dm_db_xtp_merge_requests が存在します。
> 
> この DMV を SQL Server 2016 以降が適用されなくなった。

## <a name="columns-in-the-report"></a>レポート内の列

| 列名 | データ型 | 説明 |
| :-- | :-- | :-- |
| request_state | TINYINT | マージ要求の状態。<br/>0 = Requested<br/>1 = Pending<br/>2 = インストールされています。<br/>3 = Abandoned |
| request_state_desc | nvarchar(60) | 要求の現在の状態の意味があります。<br/><br/>要求のマージ要求が存在します。<br/>保留中のマージが処理中です。<br/>マージはインストールが完了しました。<br/>-破棄されたマージを完了できませんでした、おそらくストレージの容量不足が原因です。 |
| destination_file_id | GUID | マージ元ファイルから作成するマージ先ファイルの一意な識別子。 |
| lower_bound_tsn | BIGINT | マージ先ファイルの最小のタイムスタンプ。 すべてのマージ元ファイルのうち、トランザクションのタイムスタンプが最小であるものがマージされます。 |
| upper_bound_tsn | BIGINT | マージ先ファイルの最大のタイムスタンプ。 すべてのマージ元ファイルのうち、トランザクションのタイムスタンプが最大であるものがマージされます。 |
| collection_tsn | BIGINT | 現在の行を収集できる時刻。<br/><br/>Installed 状態の行は、checkpoint_tsn が collection_tsn より大きいと削除されます。<br/><br/>Abandoned 状態の行は、checkpoint_tsn が collection_tsn より小さいと削除されます。 |
| checkpoint_tsn | BIGINT | チェックポイントが開始された時刻。<br/><br/>この値より小さいタイムスタンプを持つトランザクションによって実施されたすべての削除は、新しいデータ ファイルに反映されます。 残りの削除は、マージ先デルタ ファイルに移動されます。 |
| sourcenumber_file_id | GUID | マージ元ファイルを一意に識別する最大 16 個の内部ファイル ID。 |

## <a name="permissions"></a>アクセス許可

現在のデータベースに対する VIEW DATABASE STATE 権限が必要です。

## <a name="see-also"></a>参照

[メモリ最適化テーブルの動的管理ビュー (TRANSACT-SQL)](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)


