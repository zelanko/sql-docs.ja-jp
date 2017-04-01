---
title: "監査変換 | Microsoft Docs"
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
  - "sql13.dts.designer.audittrans.f1"
helpviewer_keywords: 
  - "パッケージの環境データ [Integration Services]"
  - "監査変換"
ms.assetid: 8c143682-9c81-4150-83d6-1d9678151d37
caps.latest.revision: 46
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 46
---
# 監査変換
  監査変換により、パッケージが実行される環境に関するデータをパッケージ内のデータ フローに含めることができます。 たとえば、パッケージ、コンピューター、および演算子の名前をデータ フローに追加できます。 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] には、この情報を提供するシステム変数が含まれています。  
  
## システム変数  
 次の表では、監査変換で使用できるシステム変数について説明します。  
  
|システム変数|インデックス|Description|  
|---------------------|-----------|-----------------|  
|**ExecutionInstanceGUID**|0|パッケージの実行インスタンスを識別する GUID です。|  
|**PackageID**|1|パッケージの一意識別子です。|  
|**PackageName**|2|パッケージの名前です。|  
|**VersionID**|3|パッケージのバージョンです。|  
|**ExecutionStartTime**|4|パッケージの実行を開始した時刻です。|  
|**MachineName**|5|コンピューター名|  
|**UserName**|6|パッケージを開始した人のログイン名です。|  
|**TaskName**|7|監査変換が関連付けられているデータ フロー タスクの名前です。|  
|**TaskId**|8|データ フロー タスクの一意識別子です。|  
  
## 監査変換の構成  
 監査変換を構成するには、新しい出力列の名前を設定し、変換出力に追加します。次に、その出力列にシステム変数をマップします。 1 つのシステム変数は、複数の列にマップできます。  
  
 この変換は 1 つの入力と 1 つの出力をとります。 エラー出力はサポートされていません。  
  
 プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 **[監査変換エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、「 [Audit Transformation Editor](../../../integration-services/data-flow/transformations/audit-transformation-editor.md)」を参照してください。  
  
 **[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。 **[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [共通プロパティ](../Topic/Common%20Properties.md)  
  
-   [変換のカスタム プロパティ](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)  
  
 プロパティの設定方法の詳細については、「[データ フロー コンポーネントのプロパティを設定する](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)」を参照してください。  
  
  