---
title: Data Quality Client で Integration Services (SSIS) プロジェクトを開く
description: SQL Server Data Quality Services の Data Quality Client を使用して SQL Server Integration Services (SSIS) プロジェクトを開く方法について説明します。
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: a8bad2f1-8fb0-4d14-a978-11a5720e62d6
author: swinarko
ms.author: sawinark
ms.openlocfilehash: cc20a282743d83873b58914e4fa391b8402ce473
ms.sourcegitcommit: 6be9a0ff0717f412ece7f8ede07ef01f66ea2061
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85809773"
---
# <a name="open-integration-services-projects-in-data-quality-client"></a>Data Quality Client で Integration Services プロジェクトを開く

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  Integration Services の DQS クレンジングコンポーネントでは、クレンジングプロジェクトをバッチモードで実行できます。 しかし、DQS のデータ品質プロジェクト内のクレンジング アクティビティの **[結果の管理と表示]** タブでクレンジング結果を確認するのと同様の方法で、Integration Services パッケージ内でクレンジング結果を確認したい場合があります。 DQS では、 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] [プロジェクトを開く] **画面から他のデータ品質プロジェクトを開くのと同様に、** で Integration Services プロジェクトを開くことができ、Integration Services プロジェクト内のクレンジング結果について、インタラクティブなクレンジングを操作できます。  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> 制限事項と制約事項  
  
-   完了した Integration Services プロジェクトだけが **の** [プロジェクトを開く] [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]画面に表示されます。 失敗したプロジェクトや実行中のプロジェクトは **[プロジェクトを開く]** 画面に表示されません。  
  
-   Integration Services プロジェクトは、**で、インタラクティブなクレンジング ステージとして (** [管理ビューと結果] [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]タブで) 開きます。 **[最適化]** タブまたは **[マップ]** タブに移動することはできません。 **[次へ]** をクリックして **[エクスポート]** タブにだけ移動できます。  
  
-   ロックされた Integration Services プロジェクトを [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]から削除することはできません。 削除するには先にロックを解除する必要があります。  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> 必要条件  
 Integration Services プロジェクトを [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]に表示して開くためには、DQS クレンジング コンポーネントのパッケージを含む Integration Services プロジェクトの実行を正常に完了させる必要があります。  
  
###  <a name="security"></a><a name="Security"></a> セキュリティ  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Integration Services プロジェクトを開くためには、DQS_MAIN データベースに対する dqs_kb_editor または dqs_kb_operator ロールが必要です。  
  
  
##  <a name="open-an-integration-services-project"></a><a name="Open"></a> Integration Services プロジェクトを開く  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Data Quality Client アプリケーションを実行](../data-quality-services/run-the-data-quality-client-application.md)します。  
  
2.  の [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] ホーム画面で、[**データ品質プロジェクトを開く**] をクリックします。 **[プロジェクトを開く]** 画面が表示されます。  
  
3.  **[プロジェクトを開く]** 画面で、次のいずれかの方法で Integration Services プロジェクトを特定します。  
  
    1.  **プロジェクト名**: Integration Services プロジェクトは、次の名前付け用語を使用して一覧表示されます: "PACKAGE. DQS Cleansing_ *\<DATE>\<TIME>* _ {GUID}。" 同じパッケージを [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で正常に実行するたびに、新しいプロジェクトが **[プロジェクトを開く]** 画面に表示されます。  
  
    2.  **[プロジェクトの種類]**: Integration Services プロジェクトはプロジェクトの種類が **[SSIS]** として **[プロジェクトを開く]** 画面に表示されます。  
  
     プロジェクトを選択して **[次へ]** をクリックします。  
  
4.  Integration Services プロジェクトが、インタラクティブなクレンジング ステージとして (**[管理ビューと結果]** タブで) 開きます。 Integration Services プロジェクト内のデータに対してインタラクティブなクレンジングを実行できます。 **[結果の管理と表示]** タブについて詳しくは、「[DQS &#40;内部&#41; ナレッジを使用したデータのクレンジング](../data-quality-services/cleanse-data-using-dqs-internal-knowledge.md)」の「[インタラクティブなクレンジング ステージ](../data-quality-services/cleanse-data-using-dqs-internal-knowledge.md#Interactive)」をご覧ください。  
  
5.  **[次へ]** をクリックして **[エクスポート]** タブに進みます。ここでは処理されたデータを、SQL Server データベースの新しいテーブル、.csv ファイル、または Excel ファイルにエクスポートできます。 **[エクスポート]** タブについて詳しくは、「[DQS &#40;内部&#41; ナレッジを使用したデータのクレンジング](../data-quality-services/cleanse-data-using-dqs-internal-knowledge.md)」の「[エクスポート ステージ](../data-quality-services/cleanse-data-using-dqs-internal-knowledge.md#Export)」をご覧ください。  
  
6.  データをエクスポートした後で **[完了]** をクリックして Integration Services プロジェクトを閉じます。  

  
## <a name="see-also"></a>関連項目  
 [DQS クレンジング変換](../integration-services/data-flow/transformations/dqs-cleansing-transformation.md)   
 [Integration Services (SSIS) プロジェクト](../integration-services/integration-services-ssis-projects-and-solutions.md)  
  
  
