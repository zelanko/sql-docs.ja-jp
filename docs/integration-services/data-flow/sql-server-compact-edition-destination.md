---
title: "SQL Server Compact Edition 変換先 | Microsoft Docs"
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
  - "sql13.dts.designer.sqlservercompactdest.f1"
helpviewer_keywords: 
  - "変換先 [Integration Services], SQL Server Compact"
  - "SQL Server Compact, 変換先"
  - "挿入、データ"
ms.assetid: 697742ba-cc14-414d-8187-1845ad0dd99b
caps.latest.revision: 56
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 56
---
# SQL Server Compact Edition 変換先
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 変換先では、データが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact データベースに書き込まれます。  
  
> [!NOTE]  
>  64 ビット コンピューターでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact データ ソースに接続するパッケージを 32 ビット モードで実行する必要があります。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact データ ソースへの接続に使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact Provider は、32 ビット版でのみ使用できます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 変換先を構成するには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 変換先でデータが挿入されるテーブルの名前を指定します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 変換先のカスタム プロパティ TableName には、テーブル名が含まれます。  
  
 この変換先ではデータ ソースへの接続に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 接続マネージャーが使用され、この接続マネージャーによって、使用する OLE DB プロバイダーが指定されます。 詳細については、「[SQL Server Compact Edition 接続マネージャー](../../integration-services/connection-manager/sql-server-compact-edition-connection-manager.md)」を参照してください。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 変換先には、パッケージの読み込み時にプロパティ式で更新できる、TableName カスタム プロパティがあります。 詳細については、「[Integration Services (SSIS) の式](../../integration-services/expressions/integration-services-ssis-expressions.md)」、「[パッケージでプロパティ式を使用する](../../integration-services/expressions/use-property-expressions-in-packages.md)」、および「[SQL Server Compact Edition 変換先のカスタム プロパティ](../../integration-services/data-flow/sql-server-compact-edition-destination-custom-properties.md)」を参照してください。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 変換先の入力は 1 つで、エラー出力はサポートされていません。  
  
## SQL Server Compact Edition 変換先の構成  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 **[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。 **[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [共通プロパティ](../Topic/Common%20Properties.md)  
  
-   [SQL Server 変換先のカスタム プロパティ](../../integration-services/data-flow/sql-server-destination-custom-properties.md)  
  
## 関連タスク  
 このコンポーネントのプロパティの設定方法の詳細については、「[データ フロー コンポーネントのプロパティを設定する](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)」を参照してください。  
  
## 参照  
 [データ フロー](../../integration-services/data-flow/data-flow.md)  
  
  