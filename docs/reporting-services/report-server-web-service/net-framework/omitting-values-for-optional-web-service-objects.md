---
title: 省略可能な Web サービス オブジェクトの値を省略 | Microsoft Docs
description: レポート サーバー Web サービスの複合型の一部のプロパティは、Specified プロパティをサポートしています。これにより、一部の書き込み可能なプロパティの値を省略できます。
ms.date: 03/04/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], omitted values
- XML Web service [Reporting Services], omitted values
- Report Server Web service, omitted values
- omitting values [Reporting Services]
ms.assetid: ceb68b8b-9214-4745-abc9-f47f33ecd6f7
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 3a7ea9c535092201eaa2c901ef11975bf1461d52
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "79509673"
---
# <a name="omitting-values-for-optional-web-service-objects"></a>オプションの Web サービス オブジェクトの値の省略
  レポート サーバー Web サービス複合型のプロパティには、Specified プロパティと呼ばれる付随するプロパティを持つものがあります。 このプロパティには、元のプロパティ名に "Specified" が付加された名前が割り当てられます。 このプロパティが存在することは、元のプロパティ値が省略される可能性があることを示しています。 これは、Web サービス記述言語 (WSDL) から [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] のプロキシ クラスに変換した直接的な結果です。 たとえば、複合型 <xref:ReportService2010.DataSourceDefinition.Enabled%2A> の Web サービス プロパティ <xref:ReportService2010.DataSourceDefinition> には、<xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A> という名前の付随するプロパティがあります。 アプリケーションを構築していて、<xref:ReportService2010.DataSourceDefinition.Enabled%2A> プロパティの値を設定したくない場合は、<xref:ReportService2010.DataSourceDefinition.Enabled%2A> の値を指定する必要はありません。**true** という既定値が使われます。 ただし、<xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A> は **false** に設定する必要があります。 <xref:ReportService2010.DataSourceDefinition.Enabled%2A> プロパティの値を指定する場合は、<xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A> を **true** に設定する必要があります。 これは書き込み可能なプロパティに適用されます。 読み取り専用プロパティの場合は、アクションを行う必要がありません。  
  
> [!IMPORTANT]  
>  このような方法を使用したプロパティの設定に失敗すると、予想されない Web サービスの動作が発生する可能性があります。  
  
 通常、追加の Specified プロパティの処理を必要とするデータ型は、**Boolean**、**DateTime**、および **Enumeration** です。  
  
 例については、<xref:ReportService2010.ReportingService2010.CreateDataSource%2A> メソッドを参照してください。  
  
## <a name="see-also"></a>参照  
 [Web サービスと .NET Framework を使用してのアプリケーションの構築](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [テクニカル リファレンス (SSRS)](../../../reporting-services/technical-reference-ssrs.md)  
  
  
