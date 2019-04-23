---
title: ディメンションのストレージ |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- dimensions [Analysis Services], storage
- storing data [Analysis Services]
- storage [Analysis Services], dimensions
- relational OLAP
- multidimensional OLAP
- MOLAP
- storing data [Analysis Services], dimensions
- ROLAP
ms.assetid: 8d74b932-2174-4e1f-8414-636455880b6a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ce5bf2a376712d603be3099f7ccefa0e6b799219
ms.sourcegitcommit: b87c384e10d6621cf3a95ffc79d6f6fad34d420f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/22/2019
ms.locfileid: "60154931"
---
# <a name="dimension-storage"></a>ディメンションのストレージ
  ディメンションの[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 2 つのストレージ モードをサポートします。  
  
-   リレーショナル OLAP (ROLAP)  
  
-   多次元 OLAP (MOLAP)  
  
 ストレージ モードにより、ディメンションのデータの位置と形式が決定されます。 MOLAP はディメンションの既定のストレージ モードです。 **関連トピック:**[パーティションのストレージ モードと処理](../multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md)  
  
## <a name="molap"></a>[MOLAP]  
 MOLAP を使用するディメンションのデータは、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスの多次元構造に格納されます。 この多次元構造はディメンションが処理されるときに作成および設定されます。 MOLAP ディメンションの方が、ROLAP ディメンションよりクエリ パフォーマンスは優れています。  
  
## <a name="rolap"></a>[ROLAP]  
 ROLAP を使用するディメンションのデータは、実際には、ディメンションを定義するために使用されるテーブルに格納されます。 ROLAP ストレージ モードを使用すると、クエリ パフォーマンスの点で譲歩すれば、大量のデータを複製しなくても大きなディメンションをサポートできます。 ディメンションはそのディメンションを定義するために使用されるデータ ソース ビューのテーブルに直接依存しているので、ROLAP ストレージ モードは、リアルタイム OLAP もサポートします。  
  
> [!IMPORTANT]  
>  ディメンションで ROLAP ストレージ モードが使用され、ディメンションが MOLAP ストレージを使用するキューブに含まれている場合は、元のテーブルのスキーマを変更したら、直ちにキューブを処理する必要があります。 直ちに処理しないと、キューブをクエリしたときに返される結果に一貫性がなくなることがあります。 **関連トピック:**[自動化による Analysis Services 管理タスク SSIS](../instances/automate-analysis-services-administrative-tasks-with-ssis.md)します。  
  
## <a name="see-also"></a>参照  
 [パーティションのストレージ モードおよび処理](../multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md)  
  
  
