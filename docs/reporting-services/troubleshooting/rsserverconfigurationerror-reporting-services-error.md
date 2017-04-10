---
title: "rsServerConfigurationError - Reporting Services エラー | Microsoft Docs"
ms.custom: ""
ms.date: "03/20/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "rsServerConfigurationError"
ms.assetid: 0913afc2-34b4-4713-b570-cfd5718975ac
caps.latest.revision: 12
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 12
---
# rsServerConfigurationError - Reporting Services エラー
    
## 詳細  
  
|||  
|-|-|  
|製品名|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|イベント ID|rsServerConfiguration|  
|イベント ソース|Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings|  
|コンポーネント|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|メッセージ テキスト|レポート サーバーで構成エラーが発生しました。|  
  
## 説明  
 これは、レポート サーバーまたはレポート作成ツールの構成設定が無効な場合に発生する、一般的なエラーです。 通常、このエラーは、エラーの実際の原因を示す 2 番目のメッセージと共に表示されます。  
  
 考えられる原因を次に示します。  
  
-   RSReportServer.config ファイルまたは RSReportDesigner.config ファイルが見つからないか読み取ることができません。  
  
-   一方の構成ファイル内の XML 要素が見つからないか無効です。  
  
-   1 つまたは複数の XML 要素の値が見つからないか無効です。  
  
-   レジストリ設定が無効です。  
  
## ユーザーの操作  
 構成ファイルを手動で編集した後にこのエラーが発生するようになった場合は、変更を破棄して以前の値を入力するか、バックアップがある場合は以前のバージョンを復元します。  
  
 **rsServerConfiguration** エラーに伴うエラー メッセージの詳細情報を確認するには、レポート サーバーのトレース ログ ファイルを確認します。このファイルは、\Microsoft SQL Server\MSRS12.\<instancename >\Reporting Services\LogFiles にあります。 詳細については、「[Reporting Services のログ ファイルとソース](../../reporting-services/report-server/reporting-services-log-files-and-sources.md)」を参照してください。  
  
## 内部使用のみ  
  
## 参照  
 [Reporting Services 構成ファイル](../../reporting-services/report-server/reporting-services-configuration-files.md)   
 [Reporting Services の構成ファイル &#40;RSreportserver.config&#41; の変更](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)  
  
  