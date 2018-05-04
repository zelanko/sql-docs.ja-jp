---
title: sys.sysconfigures (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-compatibility-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.sysconfigures
- sysconfigures
- sys.sysconfigures_TSQL
- sysconfigures_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysconfigures compatibility view
- sysconfigures system table
ms.assetid: 146bf10a-c898-4676-a2a1-673fb1cee7a2
caps.latest.revision: 39
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 62423ffb1f596a65fbd7a754947c2c3d04f7fb2f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="syssysconfigures-transact-sql"></a>sys.sysconfigures (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ユーザーによって設定される構成オプションごとに 1 行のデータを格納します。 **sysconfigures**の最後の起動前に定義されている構成オプションを含む[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、以降、動的な構成オプションに設定するとします。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**value**|**int**|ユーザーが変更可能な変数の値です。 これは、使用して、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] RECONFIGURE が実行された場合にのみです。|  
|**config**|**int**|構成変数番号です。|  
|**comment**|**nvarchar (255)**|この構成オプションの説明です。|  
|**ステータス**|**smallint**|構成オプションの状態を表すビットマップ。 次の値があります。<br /><br /> 0 = 静的。 設定はサーバーの再起動時に反映されます。<br /><br /> 1 = 動的。 変数は RECONFIGURE ステートメントの実行時に反映されます。<br /><br /> 2 = 詳細。 変数が表示される場合にのみ、**オプションの詳細の表示**設定されています。 設定はサーバーの再起動時に反映されます。<br /><br /> 3 = 動的および詳細。|  
  
## <a name="see-also"></a>参照  
 [システム ビューへのシステム テーブルのマッピング&#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [互換性ビュー &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
