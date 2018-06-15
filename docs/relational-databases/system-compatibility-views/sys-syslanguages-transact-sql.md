---
title: sys.syslanguages (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-compatibility-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.syslanguages
- sys.syslanguages_TSQL
- syslanguages
- syslanguages_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- syslanguages system table
- sys.syslanguages compatibility view
ms.assetid: f216d1cd-997c-42f0-a737-abbdfcd88383
caps.latest.revision: 37
author: rothja
ms.author: jroth
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 4c879ed679052a14d420211c5977d2152d5ccb8f
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33222073"
---
# <a name="syssyslanguages-transact-sql"></a>sys.syslanguages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに存在する言語ごとに、1 行のデータを格納します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|langid|**smallint**|一意な言語 ID。|  
|dateformat|**nchar(3)**|日付の表示順序 (例 : DMY)。|  
|datefirst|**tinyint**|週の最初の曜日。1 は月曜、2 は火曜のようになり、7 は日曜になります。|  
|upgrade|**int**|システムでの使用のため予約済み。|  
|name|**sysname**|たとえば、フランス語の公式言語名。|  
|別名 (alias)|**sysname**|言語の別名 (例 : French)。|  
|months|**nvarchar(372)**|1 月から 12 月の順に、コンマで区切った月の名前。月の名前は省略形ではなく、それぞれ 20 文字までです。|  
|shortmonths|**nvarchar(132)**|1 月から 12 月の順に、コンマで区切った月の名前。月の名前は省略形で、それぞれ 9 文字までです。|  
|日|**nvarchar(217)**|月曜から日曜の順に、コンマで区切った曜日の名前。曜日の名前はそれぞれ 30 文字までです。|  
|lcid|**int**|この言語を使用する [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のロケール ID。|  
|msglangid|**smallint**|[!INCLUDE[ssDE](../../includes/ssde-md.md)] メッセージ グループ id。|  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]次のインストールされている言語が含まれています。  
  
|英語で表した名前|Windows LCID|[!INCLUDE[ssDE](../../includes/ssde-md.md)] メッセージ グループ ID|  
|---------------------|------------------|-----------------------------------------|  
|英語|1033|1033|  
|ドイツ語|1031|1031|  
|フランス語|1036|1036|  
|日本語|1041|1041|  
|デンマーク語|1030|1030|  
|スペイン語|3082|3082|  
|イタリア語|1040|1040|  
|オランダ語|1043|1043|  
|ノルウェー語|2068|2068|  
|ポルトガル語|2070|2070|  
|フィンランド語|1035|1035|  
|スウェーデン語|1053|1053|  
|チェコ語|1029|1029|  
|ハンガリー語|1038|1038|  
|ポーランド語|1045|1045|  
|ルーマニア語|1048|1048|  
|クロアチア語|1050|1050|  
|スロバキア語|1051|1051|  
|スロヴェニア語|1060|1060|  
|ギリシャ語|1032|1032|  
|ブルガリア語|1026|1026|  
|ロシア語|1049|1049|  
|トルコ語|1055|1055|  
|英語 (U.K.)|2057|1033|  
|エストニア語|1061|1061|  
|ラトビア語|1062|1062|  
|リトアニア語|1063|1063|  
|ブラジル|1046|1046|  
|繁体字中国語|1028|1028|  
|韓国語|1042|1042|  
|簡体字中国語|2052|2052|  
|アラビア語|1025|1025|  
|タイ語|1054|1054|  
  
## <a name="see-also"></a>参照  
 [互換性ビュー &#40;TRANSACT-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)   
 [システム ビューへのシステム テーブルのマッピング&#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)  
  
  
