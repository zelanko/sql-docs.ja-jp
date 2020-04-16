---
title: bandwidth_usage (Azure SQL データベース) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/28/2019
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- bandwidth_usage
- sys.bandwidth_usage
- bandwidth_usage_TSQL
- sys.bandwidth_usage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.bandwidth_usage
- bandwidth_usage
ms.assetid: 43ed8435-f059-4907-b5c0-193a258b394a
author: julieMSFT
ms.author: jrasnick
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: ea963c07a15cd5c2db3cca113680026d3100936b
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/15/2020
ms.locfileid: "67942573"
---
# <a name="sysbandwidth_usage-azure-sql-database"></a>sys.bandwidth_usage (Azure SQL Database)

[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

> [!NOTE]
> これは V11 にのみ[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]適用されます。  
  
 ** [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V11 データベース サーバー**の各データベースで使用されるネットワーク帯域幅に関する情報を返します。 指定のデータベースに対して返される各行は、1 時間にわたる 1 つの方向とクラスの使用状況をまとめたものです。  
  
 **これは、 で推奨されていません[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。**  
  
 **sys.bandwidth_usage**ビューには、次の列が含まれています。  
  
|列名|説明|  
|-----------------|-----------------|  
|**time**|帯域幅が使用されていた時間。 このビューの行は、1 時間単位です。 たとえば、2009-09-19 02:00: 00.000 は、帯域幅が 2009 年 9 月 19 日午前 2:00 から午前 3:00 までの間に使用された ことを示します。|  
|**database_name**|帯域幅を使用したデータベースの名前。|  
|**direction**|使用された帯域幅の種類で、次のいずれかになります。<br /><br /> 入力: に移動するデータ。 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]<br /><br /> 出力: から移動しているデータ。 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**class**|使用された帯域幅のクラス。次のどちらかです。<br />内部: Azure プラットフォーム内で移動しているデータ。<br />外部: Azure プラットフォームから移動するデータ。<br /><br /> このクラスは、データベースで、地域 ([!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)]) 間の連続コピー リレーションシップが進行中である場合に返されます。 特定のデータベースが連続コピー関係に関与していない場合、"インターリンク" 行は返されません。 詳細については、後の「解説」を参照してください。|  
|**time_period**|使用が発生した時間帯は、Peak または OffPeak です。 Peak 時間は、サーバーが作成された地域に基づいています。 たとえば、 サーバーが "US_Northwest" リージョンで作成された場合、Peak 時間帯は太平洋標準時の午前 10:00 から 午後 6 時まで  (太平洋標準時)。|  
|**量**|使用された帯域幅の量 (KB 単位)。|  
  
## <a name="permissions"></a>アクセス許可

 このビューは **、master**データベース内でサーバー レベルのプリンシパル ログインでのみ使用できます。  
  
## <a name="remarks"></a>解説  
  
### <a name="external-and-internal-classes"></a>外部クラスと内部クラス

 **sys.bandwidth_usage**ビューは、特定の時刻に使用されるデータベースごとに、帯域幅の使用のクラスと方向を示す行を返します。 次の例は、指定されたデータベースに対して公開される可能性があるデータを示しています。 この例では、時刻は 2012-04-21 17:00:00 になっています。これは、ピーク タイムの時間帯における発生時刻です。 データベース名は Db1 です。 この例では **、sys.bandwidth_usage**は、次のように、入力方向と出力方向と外部クラスと内部クラスの 4 つの組み合わせすべてについて行を返しました。  
  
|time|database_name|direction|class|time_period|数量|  
|----------|--------------------|---------------|-----------|------------------|--------------|  
|2012-04-21 17:00:00|Db1|イングレス|外部|Peak|66|  
|2012-04-21 17:00:00|Db1|エグレス|外部|Peak|741|  
|2012-04-21 17:00:00|Db1|イングレス|内部|Peak|1052|  
|2012-04-21 17:00:00|Db1|エグレス|内部|Peak|3525|  
  
### <a name="interpreting-data-direction-for-ssgeodr"></a>[!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)]でのデータ方向の解釈

 [!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)]の場合、帯域幅の使用状況データは連続コピー リレーションシップの両側にある論理マスター データベースで確認できます。 したがって、クエリを実行するデータベースの観点から、入力方向と出力方向インジケーターを解釈する必要があります。 たとえば、ソース サーバーからターゲット サーバーへ、1 MB のデータを転送するレプリケーション ストリームについて考えてみます。 この場合、ソース サーバーでは 1 MB が送信されたデータの総数にカウントされ、ターゲット サーバーでは 1MB が受信データとして記録されます。  
  
> [!NOTE]  
> 転送されるデータの大部分は、ソース サーバーからターゲット サーバーに、ユーザー データ フローの方向に転送されます。 ただし、一部のデータ転送では他の方向が必要になる場合があります。  
