---
title: "Analysis Services のプロジェクトでの XML の表示 (SSDT) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プロジェクト [Analysis Services]、XML の表示"
ms.assetid: dd1a4bc6-57b5-47df-8619-09f921aa6351
caps.latest.revision: 14
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 14
---
# Analysis Services のプロジェクトでの XML の表示 (SSDT)
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のデータベースをプロジェクト モードで操作している場合は、[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] によって各オブジェクトの XML 定義がプロジェクト フォルダー内に作成されます。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 内で各オブジェクトの XML ファイルの内容を見ることができます。 また、XML ファイルを直接編集することもできますが、変更によって XML を [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] で読み取れなくなる可能性があるため、ほとんどの状況ではお勧めできません。  
  
> [!NOTE]  
>  オブジェクトごとにファイルが異なるため、プロジェクト全体の xml コードは表示できませんが、各オブジェクトのコードを確認します。 プロジェクト全体のコードを表示するには、プロジェクトをビルドして、\<プロジェクト名>.asdatabase ファイルで ASSL コードを表示するしかありません。  
  
### オブジェクトの XML コードを表示するには  
  
1.  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] プロジェクトを開きます。  
  
2.  ソリューション エクスプローラーでオブジェクトを右クリックし、**[コードの表示]** をクリックします。  
  
     オブジェクトの XML コードが [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] に表示されます。  
  
## 参照  
 [Analysis Services プロジェクトのビルド &#40;SSDT&#41;](../../analysis-services/multidimensional-models/build-analysis-services-projects-ssdt.md)  
  
  