---
title: ディメンションのストレージ |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
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
caps.latest.revision: 30
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6462ebf90b7783260f7027d82b26be117ea0b5ce
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37153113"
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
  
  
