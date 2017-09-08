---
title: "データ処理拡張機能の配置 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/18/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- data processing extensions [Reporting Services], deploying
- Extension element
- deploying [Reporting Services], extensions
ms.assetid: e5c0b5a9-1386-47cb-aade-96653ecfaa54
caps.latest.revision: 34
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: dbf0fd628630b51b3e8847539888d46c0c8a590e
ms.contentlocale: ja-jp
ms.lasthandoff: 08/12/2017

---
# <a name="deploying-a-data-processing-extension"></a>データ処理拡張機能の配置
  書き込み、コンパイルした後、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]にデータ処理拡張機能、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]ライブラリ、およびレポート デザイナー、レポート サーバーで検出できるようにする必要があります。 これは、適切なディレクトリに拡張機能をコピーし、適切な [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 構成ファイルにエントリを追加するだけで簡単に行うことができます。  
  
## <a name="configuration-file-extension-element"></a>構成ファイルの Extension 要素  
 レポート サーバーまたはレポート デザイナーに配置するデータ処理拡張機能として入力する必要がある**拡張子**構成ファイル内の要素。 構成ファイルは、レポート サーバーの場合は RSReportServer.config、レポート デザイナーの場合は RSReportDesigner.config です。  
  
 次の表に、属性、**拡張子**データ処理拡張機能の要素。  
  
|属性|Description|  
|---------------|-----------------|  
|**名前**|拡張機能の一意な名前。たとえば、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ処理拡張機能に対して "SQL"、OLE DB データ処理拡張機能に対して "OLEDB"。 **Name** 属性の最大文字数は 255 文字です。 名前は、構成ファイルの **Extension** 要素内にあるすべてのエントリの間で一意にする必要があります。|  
|**型**|アセンブリの名前と共に完全修飾名前空間を含むコンマ区切りの一覧。|  
|**[表示]**|値**false**データ処理拡張機能が表示されないことのユーザー インターフェイスでことを示します。 この属性が指定されない場合、既定値は **true**になります。|  
  
 詳細については、RSReportServer.config ファイルまたは RSReportDesigner.config ファイルについて、次を参照してください。 [Reporting Services の構成ファイル](../../../reporting-services/report-server/reporting-services-configuration-files.md)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|Description|  
|-----------|-----------------|  
|[方法: レポート サーバーにデータ処理拡張機能の配置](../../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension-to-a-report-server.md)|レポート サーバーにデータ処理拡張機能を配置する方法について説明します。|  
|[方法: レポート デザイナーにデータ処理拡張機能の配置](../../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension-to-report-designer.md)|レポート デザイナーにデータ処理拡張機能を配置する方法について説明します。|  
  
## <a name="see-also"></a>参照  
 [Reporting Services 拡張機能](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [データ処理拡張機能の実装](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Reporting Services 拡張機能ライブラリ](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
