---
title: "ナレッジのインポートとエクスポート | Microsoft Docs"
ms.custom: 
ms.date: 07/31/2012
ms.prod: sql-non-specified
ms.prod_service: data-quality-services
ms.service: 
ms.component: data-quality-services
ms.reviewer: 
ms.suite: sql
ms.technology: data-quality-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 12537c9d-31e4-40b0-a411-cb343abbe96a
caps.latest.revision: "10"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 13ca99cdb38d8fced0eae2b655f1d1b2df7b9b03
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="importing-and-exporting-knowledge"></a>ナレッジのインポートとエクスポート
  [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] アプリケーションで直接ナレッジ ベースとドメインを作成するか、ナレッジ ベースにナレッジをインポートしたり、ナレッジ ベースからナレッジをエクスポートすることができます。 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] アプリケーションでは、インポートおよびエクスポート操作にデータ ファイルを使用したり、インポート操作に Excel ファイルを使用できます。 使用されるデータ ファイルは、.dqs 拡張子を持つ [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) で作成された暗号化ファイルです。 Microsoft Excel で作成されるファイルの拡張子は、.xlsx、.xls、または .csv です。 これらの操作を行うことで、データのクレンジングと照合の実行に使用するナレッジを構築および共有する際の柔軟性が高まります。  
  
> [!IMPORTANT]  
>  コマンド プロンプトで DQSInstaller.exe を実行して、 *内のすべての*[!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] ナレッジ ベースを DQS バックアップ ファイル (.dqsb) に一度にエクスポートできます。 同様に、コマンド プロンプトで DQSInstaller.exe ファイルを実行して、*すべての* ナレッジ ベースを DQS バックアップ ファイル (.dqsb) から [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] へ一度にインポートできます。 詳細については、DQS インストール ガイドの「 [Export and Import DQS Knowledge Bases Using DQSInstaller.exe](../data-quality-services/install-windows/export-and-import-dqs-knowledge-bases-using-dqsinstaller-exe.md) 」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 次のインポート操作とエクスポート操作を実行することができます。  
  
|||  
|-|-|  
|ナレッジ ベースのドメインを .dqs データ ファイルにエクスポートする|[ドメインを .dqs ファイルにエクスポートする](../data-quality-services/export-a-domain-to-a-dqs-file.md)|  
|ドメインを .dqs データ ファイルから既存のナレッジ ベースへインポートする|[ドメインを .dqs ファイルからインポートする](../data-quality-services/import-a-domain-from-a-dqs-file.md)|  
|ナレッジ ベース全体を .dqs データ ファイルにエクスポートする|[ナレッジ ベースを .dqs ファイルにエクスポートする](../data-quality-services/export-a-knowledge-base-to-a-dqs-file.md)|  
|ナレッジ ベース全体を .dqs データ ファイルにインポートする|[ナレッジ ベースを .dqs ファイルからインポートする](../data-quality-services/import-a-knowledge-base-from-a-dqs-file.md)|  
|値を Excel ファイルからドメインへインポートする|[Import Values from an Excel File into a Domain](../data-quality-services/import-values-from-an-excel-file-into-a-domain.md)|  
|ドメインを Excel ファイルからナレッジ ベースへインポートする|[ナレッジ検出でドメインを Excel ファイルからインポートする](../data-quality-services/import-domains-from-an-excel-file-in-knowledge-discovery.md)|  
|ナレッジ ベースへのクレンジング中に収集されたナレッジをインポートする|[クレンジング プロジェクトの値をドメインにインポートする](../data-quality-services/import-cleansing-project-values-into-a-domain.md)|  
  
## <a name="related-tasks"></a>関連タスク  
  
|タスクの説明|トピック|  
|----------------------|-----------|  
|ナレッジ検出を実行し、対話方式でナレッジを管理して、ナレッジ ベースを構築します。|[ナレッジ ベースの作成](../data-quality-services/building-a-knowledge-base.md)|  
|単一ドメインを作成し、ナレッジをドメインに追加します。|[ドメインの管理](../data-quality-services/managing-a-domain.md)|  
|複合ドメインを作成し、ナレッジをドメインに追加します。|[複合ドメインの管理](../data-quality-services/managing-a-composite-domain.md)|  
  
  
