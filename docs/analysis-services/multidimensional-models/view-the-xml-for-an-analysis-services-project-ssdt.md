---
title: "ビュー、XML では、Analysis Services のプロジェクト (SSDT) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: projects [Analysis Services], viewing XML
ms.assetid: dd1a4bc6-57b5-47df-8619-09f921aa6351
caps.latest.revision: "14"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f25a2d11b8ae85ea7a393364f9cc11da36ea5502
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="view-the-xml-for-an-analysis-services-project-ssdt"></a>Analysis Services のプロジェクトでの XML の表示 (SSDT)
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のデータベースをプロジェクト モードで操作している場合は、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] によって各オブジェクトの XML 定義がプロジェクト フォルダー内に作成されます。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]内で各オブジェクトの XML ファイルの内容を見ることができます。 また、XML ファイルを直接編集することもできますが、変更によって XML を [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で読み取れなくなる可能性があるため、ほとんどの状況ではお勧めできません。  
  
> [!NOTE]  
>  オブジェクトごとにファイルが異なるため、プロジェクト全体の xml コードは表示できませんが、各オブジェクトのコードを確認します。 プロジェクトをビルドし、ASSL を表示するのには、プロジェクト全体のコードを表示する唯一の方法のコードで、\<プロジェクト名 > .asdatabase ファイル。  
  
### <a name="to-view-the-xml-code-for-an-object"></a>オブジェクトの XML コードを表示するには  
  
1.  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]プロジェクトを開きます。  
  
2.  ソリューション エクスプローラーでオブジェクトを右クリックし、 **[コードの表示]**をクリックします。  
  
     オブジェクトの XML コードが [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]に表示されます。  
  
## <a name="see-also"></a>参照  
 [Analysis Services プロジェクトのビルド &#40;SSDT&#41;](../../analysis-services/multidimensional-models/build-analysis-services-projects-ssdt.md)  
  
  
