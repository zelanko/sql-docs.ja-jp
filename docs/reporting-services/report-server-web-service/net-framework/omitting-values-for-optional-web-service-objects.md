---
title: "省略可能な Web サービス オブジェクトの値を省略 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
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
- Web service [Reporting Services], omitted values
- XML Web service [Reporting Services], omitted values
- Report Server Web service, omitted values
- omitting values [Reporting Services]
ms.assetid: ceb68b8b-9214-4745-abc9-f47f33ecd6f7
caps.latest.revision: 36
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 727d9ccd8cd1e40d89cfe74291edae92988b407c
ms.openlocfilehash: 3532a470bd036e0128a8df21ca391210cf7209a2
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="omitting-values-for-optional-web-service-objects"></a>オプションの Web サービス オブジェクトの値の省略
  レポート サーバー Web サービス複合型のいくつかのプロパティには、指定したプロパティと呼ばれる付随するプロパティが存在します。 このプロパティには、元のプロパティ名に "Specified" が付加された名前が割り当てられます。 このプロパティが存在することは、元のプロパティ値が省略される可能性があることを示しています。 これは、Web サービス記述言語 (WSDL) から [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] のプロキシ クラスに変換した直接的な結果です。 たとえば、複合型 <xref:ReportService2010.DataSourceDefinition.Enabled%2A> の Web サービス プロパティ <xref:ReportService2010.DataSourceDefinition> には、<xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A> という名前の付随するプロパティがあります。 アプリケーションを構築し、値を設定したくない場合、<xref:ReportService2010.DataSourceDefinition.Enabled%2A>プロパティがありませんの値を指定する<xref:ReportService2010.DataSourceDefinition.Enabled%2A>; の既定値**true**を使用します。 ただし、する必要があります設定<xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A>に**false**です。 値を指定する場合、<xref:ReportService2010.DataSourceDefinition.Enabled%2A>プロパティを設定する必要があります<xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A>と等しい**true**です。 これは書き込み可能なプロパティに適用されます。 読み取り専用プロパティの場合は、アクションを行う必要がありません。  
  
> [!IMPORTANT]  
>  このような方法を使用したプロパティの設定に失敗すると、予想されない Web サービスの動作が発生する可能性があります。  
  
 通常追加の指定したプロパティを処理することが必要なデータ型は**ブール**、 **DateTime**、および**列挙**です。  
  
 例については、<xref:ReportService2010.ReportingService2010.CreateDataSource%2A> メソッドを参照してください。  
  
## <a name="see-also"></a>参照  
 [Web サービスと、.NET Framework を使用してアプリケーションの構築](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [テクニカル リファレンス & #40 です。SSRS &#41;](../../../reporting-services/technical-reference-ssrs.md)  
  
  
