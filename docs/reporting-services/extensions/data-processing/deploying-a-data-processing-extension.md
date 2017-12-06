---
title: "データ処理拡張機能の配置 | Microsoft Docs"
ms.custom: 
ms.date: 03/18/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: extensions
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- data processing extensions [Reporting Services], deploying
- Extension element
- deploying [Reporting Services], extensions
ms.assetid: e5c0b5a9-1386-47cb-aade-96653ecfaa54
caps.latest.revision: "34"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: e80bece5d41ca02559db4daec089c89aea43aafa
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="deploying-a-data-processing-extension"></a>データ処理拡張機能の配置
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のデータ処理拡張機能は、作成して [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] ライブラリにコンパイルした後、レポート サーバーおよびレポート デザイナーで検出できるようにする必要があります。 これは、適切なディレクトリに拡張機能をコピーし、適切な [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 構成ファイルにエントリを追加するだけで簡単に行うことができます。  
  
## <a name="configuration-file-extension-element"></a>構成ファイルの Extension 要素  
 レポート サーバーまたはレポート デザイナーに配置するデータ処理拡張機能は、構成ファイルに **Extension** 要素として入力する必要があります。 構成ファイルは、レポート サーバーの場合は RSReportServer.config、レポート デザイナーの場合は RSReportDesigner.config です。  
  
 次の表では、データ処理拡張機能の **Extension** 要素の属性について説明します。  
  
|属性|Description|  
|---------------|-----------------|  
|**名前**|拡張機能の一意な名前。たとえば、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ処理拡張機能に対して "SQL"、OLE DB データ処理拡張機能に対して "OLEDB"。 **Name** 属性の最大文字数は 255 文字です。 名前は、構成ファイルの **Extension** 要素内にあるすべてのエントリの間で一意にする必要があります。|  
|**型**|アセンブリの名前と共に完全修飾名前空間を含むコンマ区切りの一覧。|  
|**[表示]**|**false** の値は、データ処理拡張機能がユーザー インターフェイスに表示されないことを示します。 この属性が指定されない場合、既定値は **true**になります。|  
  
 RSReportServer.config ファイルまたは RSReportDesigner.config ファイルの詳細については、「[Reporting Services 構成ファイル](../../../reporting-services/report-server/reporting-services-configuration-files.md)」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|Description|  
|-----------|-----------------|  
|[データ処理拡張機能をレポート サーバーに配置する方法](../../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension-to-a-report-server.md)|レポート サーバーにデータ処理拡張機能を配置する方法について説明します。|  
|[データ処理拡張機能をレポート デザイナーに配置する方法](../../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension-to-report-designer.md)|レポート デザイナーにデータ処理拡張機能を配置する方法について説明します。|  
  
## <a name="see-also"></a>参照  
 [Reporting Services の拡張機能](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [データ処理拡張機能の実装](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Reporting Services 拡張機能ライブラリ](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
