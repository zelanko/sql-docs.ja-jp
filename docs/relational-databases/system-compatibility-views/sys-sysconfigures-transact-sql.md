---
title: "sys.sysconfigures (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-compatibility-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.sysconfigures
- sysconfigures
- sys.sysconfigures_TSQL
- sysconfigures_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sys.sysconfigures compatibility view
- sysconfigures system table
ms.assetid: 146bf10a-c898-4676-a2a1-673fb1cee7a2
caps.latest.revision: "39"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 56630c142d0227e10e6154d70902d63f204103a4
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="syssysconfigures-transact-sql"></a>sys.sysconfigures (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ユーザーによって設定される構成オプションごとに 1 行のデータを格納します。 **sysconfigures**の最後の起動前に定義されている構成オプションを含む[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、以降、動的な構成オプションに設定するとします。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**値**|**int**|ユーザーが変更可能な変数の値です。 これは、使用して、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] RECONFIGURE が実行された場合にのみです。|  
|**構成**|**int**|構成変数番号です。|  
|**コメント**|**nvarchar (255)**|この構成オプションの説明です。|  
|**ステータス**|**smallint**|構成オプションの状態を表すビットマップ。 次の値があります。<br /><br /> 0 = 静的。 設定はサーバーの再起動時に反映されます。<br /><br /> 1 = 動的。 変数は RECONFIGURE ステートメントの実行時に反映されます。<br /><br /> 2 = 詳細。 変数が表示される場合にのみ、**オプションの詳細の表示**設定されています。 設定はサーバーの再起動時に反映されます。<br /><br /> 3 = 動的および詳細。|  
  
## <a name="see-also"></a>参照  
 [システム ビュー &#40; をシステム テーブルのマッピングTRANSACT-SQL と #41 です。](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [互換性ビュー &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
