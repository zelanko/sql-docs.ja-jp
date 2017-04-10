---
title: "レポート実行の確認 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "監査 [Reporting Services]"
  - "レポート実行の確認"
  - "ログ [Reporting Services], レポート実行の確認"
  - "レポート実行データ [Reporting Services]"
  - "status information [Reporting Services]"
  - "レポート処理 [Reporting Services], 実行の確認"
  - "レポート実行のチェック"
ms.assetid: 18a98f2f-6b40-454e-9b37-568ed1a96458
caps.latest.revision: 37
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 37
---
# レポート実行の確認
  レポート処理の状態に関する情報を表示するには、ログ ファイルを使用するか、またはレポート マネージャーでレポートと共に表示される状態の情報を参照します。  
  
## レポート実行のデータ ソース  
 レポート実行ログには、レポート名、レポートを実行したユーザー名、レポート実行時間、レポートの配信に使用された配信拡張機能などの、レポート実行に関する包括的な情報が提供されます。 このデータを表示または分析するには、レポート実行ログをデータベース テーブルにコピーします。データベース テーブルでは、クエリの実行やレポートの作成を簡単に行うことができます。  
  
 ログ ファイルには、レポート実行および他のサーバー操作に関する多くのエントリが含まれます。 ログ ファイルには非常に多くのデータが含まれるので、レポートの最終実行日時のみを確認する場合は、レポート マネージャーを使用することをお勧めします。 さらに情報が必要な場合は、ログ ファイルを表示する必要があります。  
  
> [!NOTE]  
>  レポート マネージャーでは、要求時に実行されるレポートの処理時間は表示されません。  
  
 次の表では、さまざまな種類のレポートでの処理日時を表示する方法を説明します。  
  
|レポートの種類|日時情報の参照先|情報の表示に必要な操作|  
|-----------------------------|-----------------------------------------------|-----------------------------------------------|  
|レポート スナップショットとして実行するレポート|[コンテンツ] ページにあります。 詳細については、「[[コンテンツ] ページ (レポート マネージャー)](../Topic/Contents%20Page%20\(Report%20Manager\).md)」を参照してください。|1) レポートが含まれているフォルダーを見つけます。<br /><br /> 2) フォルダーを詳細表示にします。<br /><br /> 3) **[実行時]** 列の日時を記録します。|  
|レポート履歴のスナップショット|[履歴] プロパティ ページにあります。 詳細については、「[[スナップショット オプション] プロパティ ページ (レポート マネージャー)](../Topic/Snapshot%20Options%20Properties%20Page%20\(Report%20Manager\).md)」を参照してください。|1) レポートを開きます。<br /><br /> 2) **[プロパティ]** ページをクリックします。<br /><br /> 3) **[履歴]** タブをクリックします。<br /><br /> 4) **[実行時]** 列の日時を記録します。|  
|キャッシュされたレポート|キャッシュされたレポートの作成および更新に使用するスケジュールに含まれています。|1) レポートを開きます。<br /><br /> 2) **[プロパティ]** ページをクリックします。<br /><br /> 3) **[実行]** タブをクリックします。<br /><br /> 4) スケジュールを開きます。|  
  
## 参照  
 [Reporting Services のログ ファイルとソース](../../reporting-services/report-server/reporting-services-log-files-and-sources.md)   
 [レポート処理プロパティの設定](../../reporting-services/report-server/set-report-processing-properties.md)   
 [レポート マネージャー (SSRS ネイティブ モード)](../Topic/Report%20Manager%20%20\(SSRS%20Native%20Mode\).md)  
  
  