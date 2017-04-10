---
title: "rsModelGenerationError - Reporting Services エラー | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "rsModelGenerationError"
ms.assetid: 3a0ad63f-87f9-4ca1-b0c2-c85fa991634a
caps.latest.revision: 17
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 17
---
# rsModelGenerationError - Reporting Services エラー
    
## 詳細  
  
|||  
|-|-|  
|製品名|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|イベント ID|rsRenderingError|  
|イベント ソース|Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings|  
|コンポーネント|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|メッセージ テキスト|モデルの生成中にエラーが発生しました。 (rsModelGenerationError) (ReportingServicesLibrary) %1|  
  
## 説明  
 レポート モデルを生成できませんでした。  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2005 SP1 以前のバージョンでは、このエラーは、System.Data.DataSet オブジェクトでデータベース スキーマ内のテーブルまたはリレーションシップを処理できない場合に表示される可能性があります。たとえば、1 つのテーブル内の同じ列に 2 つの外部キーが定義されている場合などです。  
  
## ユーザーの操作  
 このメッセージが表示される原因となった具体的な理由を特定するには、\Microsoft SQL Server\\<SQL Server Instance\>\Reporting Services\LogFiles にあるレポート サーバーのログ ファイルを確認します。  
  
## 内部使用のみ  
  