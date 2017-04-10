---
title: "SSRS での Power BI レポートの技術プレビュー - リリース ノート | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-vnext"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4c2f20d7-a9f9-47e3-8dc3-c544a14457e0
caps.latest.revision: 5
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# Reporting Services のリリース ノート
 ||  
|-|  
|**[!INCLUDE[applies](../includes/applies-md.md)]**  SQL Server Reporting Services での Power BI レポートの技術プレビュー (2017 年 1 月)|

このトピックでは、SQL Server Reporting Services での Power BI レポートの技術プレビューの制限事項と問題について説明します。

- このリリースの新機能については、[Reporting Services の新機能](../reporting-services/sql-server-reporting-services-ssrs-の新機能.md)に関する記事を参照してください。

 **お試しください:**    
   -   [![Microsoft ダウンロード センターからダウンロードする](../analysis-services/media/download.png)](https://go.microsoft.com/fwlink/?linkid=839351)  **[Microsoft ダウンロード センターから](https://go.microsoft.com/fwlink/?linkid=839351)** SQL Server Reporting Services の Power BI レポートの技術プレビュー、および Power BI Desktop (SQL Server Reporting Services) をダウンロードする


## <a name="january--2017"></a>2017 年 1 月

### <a name="report-server"></a>レポート サーバー

- HTTPS がサポートされるようになりました。 これは 2016 年 10 月にリリースされた技術プレビュー VM では利用できなかったものです。 詳細については、「[ネイティブ モードのレポート サーバーでの SSL 接続の構成](../reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server.md)」を参照してください。
   - PowerPoint Web ビューアー アドインを使用し、その中で Power BI レポートを公開するには、HTTPS が必要です。
- スケールアウトがサポートされるようになりました。 これは 2016 年 10 月にリリースされた技術プレビュー VM では利用できなかったものです。 詳細については、[ネイティブ モード レポート サーバーのスケールアウト配置の構成](../reporting-services/install-windows/configure a native mode report server scale-out deployment.md)に関する記事を参照してください。

### <a name="power-bi-reports"></a>Power BI のレポート

- Power BI のレポートを SQL Server Reporting Services で動作させるには、Power BI Desktop (SQL Server Reporting Services) の中でレポートを作成する必要があります。 Power BI Desktop (SQL Server Reporting Services) は Evaluation Center からダウンロードできます。
- Power BI レポートは Analysis Services (テーブルまたは多次元) へのライブ接続のみをサポートしています。
- カスタム ビジュアルはサポートされていません。
- R ビジュアルはサポートされていません。