---
title: "配信拡張機能での RenderedOutputFile クラスの使用 | Microsoft Docs"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- RenderedOutputFile class
- data streams [Reporting Services]
- delivery extensions [Reporting Services], data streams
ms.assetid: 8b591801-42d5-49fa-b710-bf7e6917accf
caps.latest.revision: "34"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 1bd538d180668bdc6d4e99fb1d8246f8c4cbefaa
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="using-the-renderedoutputfile-class-for-a-delivery-extension"></a>配信拡張機能での RenderedOutputFile クラスの使用
  <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> クラスは、データ ストリームおよびデータ ストリームの関連付けられたプロパティに関する情報を表します。 <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> クラスの **Data** プロパティは、表示レポートまたはレポート リソースを **Stream** オブジェクトとして表すために使用します。  
  
 **Report** オブジェクトの <xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> メソッドは、1 つの表示レポートを一緒に構成する 1 つ以上の <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> オブジェクトの配列を返します。 1 番目の <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> オブジェクトが表示レポートです。 その他の <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> オブジェクトは、レポート データと一緒に配信される必要があるリソースです (HTML ファイルや関連付けられた画像など)。 表示拡張機能がシングル ストリーム表示拡張機能である場合は (IMAGE、PDF、MHTML、および EXCEL)、配列の <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> オブジェクトを 1 つだけ返します。  
  
 <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> クラスの使用例については、「[SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889)」 (SQL Server Reporting Services 製品サンプル) を参照してください。  
  
## <a name="see-also"></a>参照  
 [配信拡張機能の実装](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Reporting Services 拡張機能ライブラリ](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
