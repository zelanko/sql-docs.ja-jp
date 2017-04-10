---
title: "パッケージを保存する | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.savecopyas.f1"
helpviewer_keywords: 
  - "Integration Services パッケージ, 保存"
  - "パッケージ [Integration Services], 保存"
  - "パッケージの保存"
  - "SSIS パッケージ, 保存"
  - "SQL Server Integration Services パッケージ, 保存"
ms.assetid: 17c1de2c-637f-45c2-a148-79294bae0af4
caps.latest.revision: 48
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 47
---
# パッケージを保存する
  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] では、[!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーを使用してパッケージを構築し、XML ファイル (.dtsx ファイル) としてファイル システムに保存します。 パッケージ XML ファイルのコピーは、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の msdb データベースまたはパッケージ ストアに保存することもできます。 パッケージ ストアとは、[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスが管理するファイル システムの場所にあるフォルダーのことです。  
  
 ファイル システムに保存したパッケージは、後で [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスを使用して、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] またはパッケージ ストアにインポートできます。 詳細については、「[パッケージをインポートおよびエクスポートする (SSIS サービス)](../integration-services/service/import-and-export-packages-ssis-service.md)」を参照してください。  
  
 また、コマンド プロンプト ユーティリティの **dtutil** を使用して、ファイル システムと msdb 間でパッケージをコピーできます。 詳細については、「[dtutil ユーティリティ](../integration-services/dtutil-utility.md)」を参照してください。  
  
### パッケージを保存するには  
  
-   [ファイル システムにパッケージを保存する](../Topic/Save%20a%20Package%20to%20the%20File%20System.md)  
  
-   [パッケージのコピーを保存する](../Topic/Save%20a%20Copy%20of%20a%20Package.md)  
  
  