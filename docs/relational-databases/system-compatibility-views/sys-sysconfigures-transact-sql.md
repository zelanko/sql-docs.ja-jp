---
title: sys.sysconfigures (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 61936891ecd31b3bf5421a8cac49aad9f0dd37f7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47635320"
---
# <a name="syssysconfigures-transact-sql"></a>sys.sysconfigures (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ユーザーによって設定される構成オプションごとに 1 行のデータを格納します。 **sysconfigures**の最新の起動前に定義されている構成オプションを含む[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、以降、動的な構成オプションに設定します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**value**|**int**|ユーザーが変更可能な変数の値です。 これは、使用して、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] RECONFIGURE が実行された場合にのみです。|  
|**config**|**int**|構成変数番号です。|  
|**comment**|**nvarchar (255)**|この構成オプションの説明です。|  
|**status**|**smallint**|構成オプションの状態を表すビットマップ。 次の値があります。<br /><br /> 0 = 静的。 設定はサーバーの再起動時に反映されます。<br /><br /> 1 = 動的。 変数は RECONFIGURE ステートメントの実行時に反映されます。<br /><br /> 2 = 詳細。 変数が表示される場合にのみ、**詳細オプションの表示**設定されます。 設定はサーバーの再起動時に反映されます。<br /><br /> 3 = 動的および詳細。|  
  
## <a name="see-also"></a>参照  
 [システム ビューへのシステム テーブルのマッピング&#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [互換性ビュー &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
