---
title: ビュー、XML では、Analysis Services のプロジェクト (SSDT) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects [Analysis Services], viewing XML
ms.assetid: dd1a4bc6-57b5-47df-8619-09f921aa6351
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: dc3ffb73c0a13d878d68d594525f97560a586177
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="view-the-xml-for-an-analysis-services-project-ssdt"></a>Analysis Services のプロジェクトでの XML の表示 (SSDT)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]作業する場合、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]プロジェクト モードでデータベース[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]プロジェクト フォルダー内の各オブジェクトの XML 定義を作成します。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]内で各オブジェクトの XML ファイルの内容を見ることができます。 また、XML ファイルを直接編集することもできますが、変更によって XML を [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で読み取れなくなる可能性があるため、ほとんどの状況ではお勧めできません。  
  
> [!NOTE]  
>  オブジェクトごとにファイルが異なるため、プロジェクト全体の xml コードは表示できませんが、各オブジェクトのコードを確認します。 プロジェクトをビルドし、ASSL を表示するのには、プロジェクト全体のコードを表示する唯一の方法のコードで、\<プロジェクト名 > .asdatabase ファイル。  
  
### <a name="to-view-the-xml-code-for-an-object"></a>オブジェクトの XML コードを表示するには  
  
1.  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]プロジェクトを開きます。  
  
2.  ソリューション エクスプローラーでオブジェクトを右クリックし、 **[コードの表示]**をクリックします。  
  
     オブジェクトの XML コードが [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]に表示されます。  
  
## <a name="see-also"></a>参照  
 [Analysis Services プロジェクトのビルド &#40;SSDT&#41;](../../analysis-services/multidimensional-models/build-analysis-services-projects-ssdt.md)  
  
  
