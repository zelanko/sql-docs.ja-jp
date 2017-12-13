---
title: "ASSL オブジェクトとオブジェクトの特性 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- reference exceptions [Analysis Services Scripting Language]
- ASSL, objects
- inheritance [Analysis Services Scripting Language]
- localized names [Analysis Services Scripting Language]
- objects [Analysis Services Scripting Language]
- names [Analysis Services Scripting Language]
- Analysis Services Scripting Language, objects
- expansion [Analysis Services Scripting Language]
ms.assetid: 6e5c28b5-c0bc-4ccd-82e5-e174bbb71386
caps.latest.revision: "28"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 2a3dc1f15f445d24522911a8d21b32e8d8ac6ca3
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="assl-objects-and-object-characteristics"></a>ASSL オブジェクトとオブジェクトの特性
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Analysis Services スクリプト言語 (ASSL) のオブジェクトでは、オブジェクトのグループ、継承、名前付け、拡張、および処理に関して特定のガイドラインに従います。  
  
## <a name="object-groups"></a>オブジェクト グループ  
 すべて[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]オブジェクトが、XML 表現を作成します。 オブジェクトは 2 つのグループに分けられます。  
  
 **主要なオブジェクト**  
 主要なオブジェクトは、個別に作成、変更、削除することができます。 主要なオブジェクトは次のとおりです。  
  
-   サーバー  
  
-   データベース  
  
-   ディメンション  
  
-   キューブ  
  
-   メジャー グループ  
  
-   パーティション  
  
-   パースペクティブ  
  
-   [マイニング モデル]  
  
-   ロール  
  
-   サーバーまたはデータベースに関連付けられているコマンド  
  
-   データ ソース  
  
 主要なオブジェクトには、その履歴と状態を追跡するための次のプロパティがあります。  
  
-   **CreatedTimestamp**  
  
-   **LastSchemaUpdate**  
  
-   **LastProcessed** (必要な場合)  
  
> [!NOTE]  
>  オブジェクトを主要なオブジェクトとして分類すると、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のインスタンスによるオブジェクトの処理方法と、オブジェクト定義言語でのオブジェクトの処理方法に影響を与えます。 ただし、この分類によって、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 管理ツールおよび開発ツールでこれらのオブジェクトを単独作成、修正、または削除できることが保証されるわけではありません。  
  
 **マイナー オブジェクト**  
 マイナー オブジェクトは、主要な親オブジェクトの作成、変更、または削除の一部としてのみ、作成、変更、または削除を行うことができます。 マイナー オブジェクトは次のとおりです。  
  
-   階層とレベル  
  
-   属性  
  
-   メジャー  
  
-   マイニング モデル列  
  
-   キューブに関連付けられているコマンド  
  
-   集計  
  
## <a name="object-expansion"></a>オブジェクトの展開  
 **ObjectExpansion**制限は、サーバーによって返される ASSL XML の展開の次数を制御するために使用できます。 次の表には、この制限のオプションを示します。  
  
|列挙値|許可\<Alter >|Description|  
|-----------------------|---------------------------|-----------------|  
|*ReferenceOnly*|いいえ|要求されたオブジェクトおよび含まれているすべての主要なオブジェクトの名前、ID、およびタイムスタンプだけを再帰的に返します。|  
|*ObjectProperties*|はい|要求されたオブジェクトと含まれいているマイナー オブジェクトを展開し、含まれている主要なオブジェクトは返しません。|  
|*ExpandObject*|いいえ|同じ*ObjectProperties*名前、ID、および含まれる主要なオブジェクトのタイムスタンプも返されます。|  
|*ExpandFull*|はい|要求されたオブジェクトと含まれているすべてのオブジェクトを再帰的に完全に展開します。|  
  
 この ASSL 参照セクションについて説明、 *ExpandFull*表現します。 他のすべての**ObjectExpansion**レベルは、このレベルから派生します。  
  
## <a name="object-processing"></a>オブジェクト処理  
 ASSL には、読み取り専用の要素またはプロパティが含まれています (たとえば、 **LastProcessed**) から読み取ることができる、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンスがインスタンスにコマンド スクリプトが送信されるときに省略されます。 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]  では、読み取り専用の要素の変更された値を無視し、警告やエラーを返しません。  
  
 また、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] では、不適切なプロパティや無関係なプロパティは無視し、検証エラーを返しません。 たとえば、Y 要素に特定の値がある場合、X 要素は存在する必要があります。 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスでは、X 要素を無視し、Y 要素の値に対して X 要素を検証しません。  
  
  
