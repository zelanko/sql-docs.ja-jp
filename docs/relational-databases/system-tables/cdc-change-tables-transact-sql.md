---
title: cdc.change_tables (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- cdc.change_tables
- cdc.change_tables_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- cdc.change_tables
ms.assetid: 3525a5f5-8d8b-46a8-b334-4b7cd9fb7c21
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4432d4c45bdecc6f5e1804427770d005adde0cd5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68081279"
---
# <a name="cdcchangetables-transact-sql"></a>cdc.change_tables (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベース内の変更テーブルごとに 1 行を返します。 変更テーブルは、ソース テーブルに対して変更データ キャプチャを有効にすると作成されます。 システム テーブルに対して直接クエリを実行することは、できるだけ避けてください。 代わりに、実行、 [sys.sp_cdc_help_change_data_capture](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql.md)ストアド プロシージャ。  
  |列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|変更テーブルの ID です。 データベース内で一意です。|  
|**version**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]<br /><br /> [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] では、この列は常に 0 を返します。|  
|**source_object_id**|**int**|変更データ キャプチャが有効になっているソース テーブルの ID です。|  
|**capture_instance**|**sysname**|インスタンス固有のトラッキング オブジェクトの名前に使用されるキャプチャ インスタンスの名前です。 既定では、名前が、ソース スキーマ名の形式でソース テーブル名から派生*schemaname_sourcename*します。|  
|**start_lsn**|**binary(10)**|クエリを実行するときに、低レベルのエンドポイントを表すログ シーケンス番号 (LSN) は、変更テーブル内のデータを変更します。<br /><br /> NULL、低の = エンドポイントが確立されていません。|  
|**end_lsn**|**binary(10)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]<br /><br /> [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、この列は常に NULL を返します。|  
|**supports_net_changes**|**bit**|変更テーブルでは、差分変更クエリのサポートは有効です。|  
|**has_drop_pending**|**bit**|キャプチャ プロセスが、ソース テーブルが削除されたことの通知を受信しました。|  
|**role_name**|**sysname**|変更データへのアクセスに使用するデータベース ロールの名前。<br /><br /> NULL = ロールは使用されません。|  
|**index_name**|**sysname**|ソース テーブル内の行を一意に識別するために使用するインデックスの名前。 **index_name**ソース テーブルの主キー インデックスの名前か、または一意のインデックスの名前は、ソース テーブルで変更データ キャプチャが有効な場合を指定します。<br /><br /> NULL = 変更データ キャプチャが有効にし、変更データ キャプチャが有効にすると、一意のインデックスは指定されませんでした、ソース テーブルは主キーがありませんでした。<br /><br /> 注:主キーが存在するテーブルで変更データ キャプチャが有効な場合、変更データ キャプチャ機能は、差分変更が有効か無効かどうかに関係なく、インデックスを使用します。 変更データ キャプチャ機能を有効にした後は、主キーの変更ができません。 テーブルに主キーがない場合でも、変更データ キャプチャしますが、false に設定するのには、差分変更のみを有効にできます。 変更データ キャプチャが有効にした後は、主キーから作成できます。 変更データ キャプチャでは、主キーが使用されないため、主キーを変更することもできます。|  
|**filegroup_name**|**sysname**|変更テーブルが存在するファイル グループの名前。<br /><br /> NULL = 変更テーブルは、データベースの既定のファイル グループにします。|  
|**create_date**|**datetime**|ソース テーブルの有効化された日付。|  
|**partition_switch**|**bit**|示すかどうか、 **SWITCH PARTITION**コマンドの**ALTER TABLE**変更データ キャプチャが有効になっているテーブルに対して実行できます。 0 は、パーティションの切り替えがブロックされていることを示します。 非パーティション テーブルは、常に 1 を返します。|  
  
## <a name="see-also"></a>関連項目  
 [sys.sp_cdc_help_change_data_capture &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql.md)  
  
  
