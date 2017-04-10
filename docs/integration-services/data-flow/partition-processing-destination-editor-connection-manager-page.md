---
title: "[パーティション処理変換先エディター] ([接続マネージャー] ページ) | Microsoft Docs"
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
  - "sql13.dts.designer.partprocessingtransformation.connection.f1"
helpviewer_keywords: 
  - "パーティション処理変換先エディター"
ms.assetid: 7add6f82-eed1-47fc-a5d7-7b91f3f24d34
caps.latest.revision: 27
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 27
---
# [パーティション処理変換先エディター] ([接続マネージャー] ページ)
   **[パーティション処理変換先エディター]** ダイアログ ボックスの **[接続マネージャー]** ページを使用すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトまたは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスへの接続を指定できます。  
  
 パーティション処理変換先の詳細については、「 [Partition Processing Destination](../../integration-services/data-flow/partition-processing-destination.md)」を参照してください。  
  
> [!NOTE]  
>  ここで説明されているタスクは、Analysis Services テーブル モデルには適用されません。  テーブル モデルで入力列をパーティション列にマップすることはできません。 代わりに Analysis Services DDL 実行タスク [Analysis Services Execute DDL Task](../../integration-services/control-flow/analysis-services-execute-ddl-task.md) を使用してパーティションを処理することができます。  
  
## オプション  
 **[ODBC 入力先エディター]**  
 既存の接続マネージャーを一覧から選択するか、**[新規作成]** をクリックして新しい接続を作成します。  
  
 **新規**  
 **[Analysis Services 接続マネージャーの追加]** ダイアログ ボックスを使用して、新しい接続を作成します。  
  
 **利用可能なパーティションの一覧**  
 処理するパーティションを選択します。  
  
 **[処理方法]**  
 処理方法を選択します。 このオプションの既定値は **[完全]**です。  
  
|値|Description|  
|-----------|-----------------|  
|[追加 (増分)]|パーティションの増分処理を実行します。|  
|Full|パーティションの完全処理を実行します。|  
|[データのみ]|パーティションの更新処理を実行します。|  
  
## 参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../integration-services/integration-services-error-and-message-reference.md)   
 [パーティション処理変換先エディター ([マッピング] ページ)](../Topic/Partition%20Processing%20Destination%20Editor%20\(Mappings%20Page\).md)   
 [[パーティション処理変換先エディター] ([詳細設定] ページ)](../Topic/Partition%20Processing%20Destination%20Editor%20\(Advanced%20Page\).md)  
  
  