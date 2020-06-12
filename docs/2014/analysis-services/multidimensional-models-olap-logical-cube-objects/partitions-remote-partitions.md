---
title: リモートパーティション |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- storage [Analysis Services], partitions
- archiving remote partitions [Analysis Services]
- partitions [Analysis Services], remote
- restoring remote partitions [Analysis Services]
- backing up remote partitions [Analysis Services]
- partitions [Analysis Services], storage
- storing data [Analysis Services], partitions
- MasterDataSourceID property
- remote partitions [Analysis Services]
ms.assetid: 63f5d9f5-c6b6-4ceb-94fe-7b6c396d10bb
author: minewiskan
ms.author: owend
ms.openlocfilehash: c564425b541ff61353b511ba09ca16fb5331ff10
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545244"
---
# <a name="remote-partitions"></a>リモート パーティション
  リモートパーティションのデータは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] パーティションとその親キューブの定義 (メタデータ) が格納されているインスタンスとは異なる Microsoft のインスタンスに格納されます。 リモート パーティションは、パーティションとその親キューブが定義されているインスタンスと同じ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスで管理されます。  
  
> [!NOTE]  
>  リモートパーティションを格納するには、コンピューターにのインスタンスが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インストールされており、パーティションが定義されているインスタンスと同じ Service Pack レベルが実行されている必要があります。 以前のバージョンの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンス上でのリモート パーティションはサポートされていません。  
  
 リモート パーティションがメジャー グループに含まれている場合、キューブのメモリおよび CPU 使用率は、メジャー グループ内のすべてのパーティション間で分散されます。 たとえば、リモート パーティションが単独で、または親キューブの処理の一部として処理される場合、そのパーティションのメモリおよび CPU 使用率の大部分は [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のリモート インスタンスで発生します。  
  
> [!NOTE]  
>  リモート パーティションを含んでいるキューブには、書き込み許可ディメンションを含めることができます。ただし、これはキューブのパフォーマンスに影響を及ぼす可能性があります。 書き込み許可ディメンションの詳細については、「[書き込み許可ディメンション](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)」を参照してください。  
  
## <a name="storage-modes-for-remote-partitions"></a>リモート パーティションのストレージ モード  
 リモート パーティションでは、ローカル パーティションで使用する多次元 OLAP (MOLAP)、ハイブリッド OLAP (HOLAP)、リレーショナル OLAP (ROLAP) のストレージ型のいずれかを使用できます。 リモート パーティションでは、プロアクティブ キャッシュも使用できます。 リモート パーティションのストレージ モードに応じて、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のリモート インスタンスに次のデータが格納されます。  
  
|||  
|-|-|  
|ストレージ型|データ|  
|[MOLAP]|パーティションの集計と、パーティションのソース データのコピー|  
|HOLAP|パーティションの集計|  
|[ROLAP]|パーティション データなし|  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の複数のインスタンスに格納された複数の MOLAP パーティションまたは HOLAP パーティションがメジャー グループに含まれる場合、キューブでは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のそれらのインスタンス間でメジャー グループのデータを分散します。  
  
## <a name="merging-remote-partitions"></a>リモート パーティションのマージ  
 リモート パーティションは、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の同一のリモート インスタンスに格納されている他のリモート パーティションとのみマージできます。 パーティションのマージの詳細については、「 [Analysis Services &#40;SSAS-多次元&#41;でのパーティションのマージ](../multidimensional-models/merge-partitions-in-analysis-services-ssas-multidimensional.md)」を参照してください。  
  
## <a name="archiving-and-restoring-remote-partitions"></a>リモート パーティションのアーカイブと復元  
 リモート パーティションのデータのアーカイブまたは復元は、リモート パーティションを格納するデータベースをアーカイブまたは復元するときに行えます。 リモート パーティションを復元せずにデータベースを復元する場合、リモート パーティションを処理しないとパーティションのデータを使用できません。 データベースのアーカイブと復元の詳細については、「 [Analysis Services データベースのバックアップと復元](../multidimensional-models/backup-and-restore-of-analysis-services-databases.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [リモートパーティション &#40;Analysis Services の作成と管理&#41;](../multidimensional-models/create-and-manage-a-remote-partition-analysis-services.md)   
 [Analysis Services オブジェクトの処理](../multidimensional-models/processing-analysis-services-objects.md)  
  
  
