---
title: "デバイス情報設定 画像の |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- images [Reporting Services], rendering
- device information settings [Reporting Services], IMAGE rendering
ms.assetid: edad9498-69f7-4726-8699-fa615f704dff
caps.latest.revision: 39
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 528ff1aac617e36ac8b3faeed0bad0981479f651
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="image-device-information-settings"></a>画像デバイス情報設定
  次の表は、IMAGE 形式で表示するためのデバイス情報設定を示しています。  
  
|設定|値|  
|-------------|-----------|  
|**列**|レポートに設定する列の数。 この値により、レポートの元の設定は上書きされます。|  
|**ColumnSpacing**|レポートに設定する列の間隔。 この値により、レポートの元の設定は上書きされます。|  
|**DpiX**|出力画像の水平方向の解像度。 既定値は **96**です。 **BMP**、 **GIF**、 **PNG**、 **TIFF** の各出力形式に適用されます。|  
|**DpiY**|出力画像の垂直方向の解像度。 既定値は **96**です。 **BMP**、 **GIF**、 **PNG**、 **TIFF** の各出力形式に適用されます。|  
|**EndPage**|表示するレポートの最後のページ。 既定値は **StartPage**の値です。|  
|**MarginBottom**|レポートに設定する下余白の値 (インチ単位)。 整数または小数の値の後に "in" を付ける必要があります (たとえば、 **1in**)。 この値により、レポートの元の設定は上書きされます。|  
|**MarginLeft**|レポートに設定する左余白の値 (インチ単位)。 整数または小数の値の後に "in" を付ける必要があります (たとえば、 **1in**)。 この値により、レポートの元の設定は上書きされます。|  
|**MarginRight**|レポートに設定する右余白の値 (インチ単位)。 整数または小数の値の後に "in" を付ける必要があります (たとえば、 **1in**)。 この値により、レポートの元の設定は上書きされます。|  
|**MarginTop**|レポートに設定する上余白の値 (インチ単位)。 整数または小数の値の後に "in" を付ける必要があります (たとえば、 **1in**)。 この値により、レポートの元の設定は上書きされます。|  
|**OutputFormat**|[!INCLUDE[ndptecgdiexpanded](../includes/ndptecgdiexpanded-md.md)] ([!INCLUDE[ndptecgdi](../includes/ndptecgdi-md.md)]) でサポートされるいずれかの出力形式。 **BMP**、 **EMF**、 **GIF**、 **JPEG**、 **PNG**、または **TIFF**です。|  
|**PageHeight**|レポートに設定するページの高さ (インチ単位)。 整数または小数の値の後に "in" を付ける必要があります (たとえば、 **11in**)。 この値により、レポートの元の設定は上書きされます。|  
|**PageWidth**|レポートに設定するページの幅 (インチ単位)。 整数または小数の値の後に "in" を付ける必要があります (たとえば、 **8.5in**)。 この値により、レポートの元の設定は上書きされます。|  
|**PrintDpiX**|出力画像の水平方向の解像度。 既定値は、 **300**です。 拡張メタファイル (**EMF**) 出力形式に適用されます。|  
|**PrintDpiY**|出力画像の垂直方向の解像度。 既定値は、 **300**です。 拡張メタファイル (**EMF**) 出力形式に適用されます。|  
|**StartPage**|表示するレポートの最初のページ。 値 **0** はすべてのページを表示することを示します。 既定値は **1**です。|  
  
## <a name="see-also"></a>参照  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [表示拡張機能にデバイス情報設定を渡す](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [RSReportServer.Config で表示拡張機能パラメーターをカスタマイズする](../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [テクニカル リファレンス &#40;SSRS&#41;](../reporting-services/technical-reference-ssrs.md)  
  
  
