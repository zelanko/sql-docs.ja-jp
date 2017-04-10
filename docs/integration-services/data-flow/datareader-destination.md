---
title: "DataReader 変換先 | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.datareaderdest.f1"
helpviewer_keywords: 
  - "DataReader 変換先"
  - "変換先 [Integration Services], DataReader"
ms.assetid: 56fcc4bf-c901-42c3-a71d-110039293431
caps.latest.revision: 30
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 30
---
# DataReader 変換先
  DataReader 変換先は、ADO.NET **DataReader** インターフェイスを使用して、データ フローのデータを公開します。 公開すると、そのデータを他のアプリケーションで使用できます。 たとえば、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポートのデータ ソースを構成して、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージの実行結果を使用できます。 構成するには、DataReader 変換先を実装するデータ フローを作成します。  
  
 プログラムで DataReader 変換先にアクセスして値を読み取る方法の詳細については、「[ローカル パッケージの出力の読み込み](../../integration-services/run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)」をご覧ください。  
  
## DataReader 変換先の構成  
 DataReader 変換先のタイムアウト値を指定して、タイムアウトが発生した場合に変換先が失敗になるようにするかどうかを指定できます。 タイムアウトは、アプリケーションが指定した時間内にデータを要求しない場合に発生します。  
  
 DataReader 変換先は 1 つの入力をとります。 エラー出力はサポートされていません。  
  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 **[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [共通プロパティ](../Topic/Common%20Properties.md)  
  
-   [DataReader 変換先のカスタム プロパティ](../../integration-services/data-flow/datareader-destination-custom-properties.md)  
  
 プロパティの設定方法の詳細については、「[データ フロー コンポーネントのプロパティを設定する](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)」を参照してください。  
  
  