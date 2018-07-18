---
title: sys.bandwidth_usage (Azure SQL データベース) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: system-catalog-views
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
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
caps.latest.revision: 21
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: e34541614f20c4fedd8a691fc3c1c13d1929fb3c
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38054430"
---
# <a name="sysbandwidthusage-azure-sql-database"></a>sys.bandwidth_usage (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  **注: これにのみ適用されます[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]V11 します。**  
  
 内の各データベースで使用されるネットワーク帯域幅に関する情報を返します、  **[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V11 の論理サーバー**、します。 指定のデータベースに対して返される各行は、1 時間にわたる 1 つの方向とクラスの使用状況をまとめたものです。  
  
 **これは非推奨で、 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 論理サーバーです。**  
  
 **Sys.bandwidth_usage**ビューには、次の列が含まれています。  
  
|Column Name|説明|  
|-----------------|-----------------|  
|**time**|帯域幅が使用されていた時間。 このビューの行は、1 時間単位です。 たとえば、2009-09-19 02:00: 00.000 は、帯域幅が 2009 年 9 月 19 日午前 2:00 から午前 3:00 までの間に使用された ことを示します。|  
|**database_name**|帯域幅を使用したデータベースの名前。|  
|**方向**|使用された帯域幅の種類。次のどちらかです。<br /><br /> イングレス: 移行するデータ[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]します。<br /><br /> エグレス: データの移動が、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]します。|  
|**class**|使用された帯域幅のクラス。次のどちらかです。<br />Azure プラットフォーム内を移動する内部エラー: データ。<br />Azure platform から移行する外部: データ。<br /><br /> このクラスは、データベースはリージョン間で連続コピー リレーションシップに関与している場合にのみ返されます ([!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)])。 連続コピー リレーションシップで、特定のデータベースが参加していない場合は、「インター リンク」行は返されません。 詳細については、後述する「解説」をご覧ください。|  
|**time_period**|使用状況が発生したときの時間帯とは、ピーク時または OffPeak のいずれかです。 Peak 時間帯は、サーバーが作成された領域に基づいています。 たとえば、 サーバーが "US_Northwest" リージョンで作成された場合、Peak 時間帯は太平洋標準時の午前 10:00 から 午後 6 時まで  定義されます。|  
|**数量**|使用された帯域幅の量 (キロバイト (KB) 単位)。|  
  
## <a name="permissions"></a>アクセス許可  
 このビューはのみ利用可能、**マスター**データベース、サーバー レベル プリンシパル ログインをします。  
  
## <a name="remarks"></a>コメント  
  
### <a name="external-and-internal-classes"></a>外部クラスと内部クラス  
 特定の時点で使用される各データベースに対して、 **sys.bandwidth_usage**ビューには、クラスと帯域幅の使用の方向を示す行が返されます。 次の例は、指定されたデータベースに対して公開される可能性があるデータを示しています。 この例では、時刻は 2012-04-21 17:00:00 になっています。これは、ピーク タイムの時間帯における発生時刻です。 データベース名は Db1 です。 この例で**sys.bandwidth_usage**受信と送信方向の外部および内部クラスでは、4 つの組み合わせをすべての行が次のように戻りました。  
  
|time|database_name|direction|class|time_period|quantity|  
|----------|--------------------|---------------|-----------|------------------|--------------|  
|2012-04-21 17:00:00|Db1|Ingress|External|Peak|66|  
|2012-04-21 17:00:00|Db1|Egress|External|Peak|741|  
|2012-04-21 17:00:00|Db1|Ingress|Internal|Peak|1052|  
|2012-04-21 17:00:00|Db1|Egress|Internal|Peak|3525|  
  
### <a name="interpreting-data-direction-for-includessgeodrincludesssgeodr-mdmd"></a>[!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)]でのデータ方向の解釈  
 [!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)]の場合、帯域幅の使用状況データは連続コピー リレーションシップの両側にある論理マスター データベースで確認できます。 したがって、クエリの対象となる論理サーバーを基準として、Ingress 方向と Egress 方向のインジケーターを解釈する必要があります。 たとえば、ソース サーバーからターゲット サーバーへ、1 MB のデータを転送するレプリケーション ストリームについて考えてみます。 この場合、ソース サーバー側では、送信した合計データ サイズに 1 MB が含まれます。また、ターゲット サーバー側では、受信したデータ サイズとして 1 MB が記録されます。  
  
> [!NOTE]  
>  ユーザー データ フローの方向では、ほとんどのデータ転送は、ソース サーバーからターゲット サーバーへの転送になります。 ただし、一部のデータ転送では他の方向が必要になる場合があります。  
  
  
