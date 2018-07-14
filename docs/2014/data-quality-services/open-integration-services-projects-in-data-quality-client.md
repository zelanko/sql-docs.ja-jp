---
title: Data Quality Client で Integration Services プロジェクトを開く | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a8bad2f1-8fb0-4d14-a978-11a5720e62d6
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8c3763ac1fa89ae69d905510944e75ec2a10116d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37217992"
---
# <a name="open-integration-services-projects-in-data-quality-client"></a>Data Quality Client で Integration Services プロジェクトを開く
  [!INCLUDE[ssDQSCleansingLong](../includes/ssdqscleansinglong-md.md)]クレンジング プロジェクトをバッチ モードで実行することができます。 しかし、DQS のデータ品質プロジェクト内のクレンジング アクティビティの **[結果の管理と表示]** タブでクレンジング結果を確認するのと同様の方法で、Integration Services パッケージ内でクレンジング結果を確認したい場合があります。 DQS では、 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] [プロジェクトを開く] **画面から他のデータ品質プロジェクトを開くのと同様に、** で Integration Services プロジェクトを開くことができ、Integration Services プロジェクト内のクレンジング結果について、インタラクティブなクレンジングを操作できます。  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="LimitationsRestrictions"></a> 制限事項と制約事項  
  
-   完了した Integration Services プロジェクトだけが **の** [プロジェクトを開く] [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]画面に表示されます。 失敗したプロジェクトや実行中のプロジェクトは **[プロジェクトを開く]** 画面に表示されません。  
  
-   Integration Services プロジェクトは、**で、インタラクティブなクレンジング ステージとして (** [管理ビューと結果] [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]タブで) 開きます。 **[最適化]** タブまたは **[マップ]** タブに移動することはできません。 **[次へ]** をクリックして **[エクスポート]** タブにだけ移動できます。  
  
-   ロックされた Integration Services プロジェクトを [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]から削除することはできません。 削除するには先にロックを解除する必要があります。  
  
###  <a name="Prerequisites"></a> 前提条件  
 Integration Services プロジェクトを [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]に表示して開くためには、DQS クレンジング コンポーネントのパッケージを含む Integration Services プロジェクトの実行を正常に完了させる必要があります。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 Integration Services プロジェクトを開くためには、DQS_MAIN データベースに対する dqs_kb_editor または dqs_kb_operator ロールが必要です。  
  
 ![上部のリンクに戻る で使用される矢印アイコン](../2014-toc/media/uparrow16x16.gif "に戻る リンクの上位で使用される矢印アイコン")[でこのトピック](#Intro)  
  
##  <a name="Open"></a> Integration Services プロジェクトを開く  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]「[Data Quality Client アプリケーションの実行](../../2014/data-quality-services/run-the-data-quality-client-application.md)」をご覧ください。  
  
2.  [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] のホーム画面で、 **[データ品質プロジェクトを開く]** をクリックします。 **[プロジェクトを開く]** 画面が表示されます。  
  
3.  **[プロジェクトを開く]** 画面で、次のいずれかの方法で Integration Services プロジェクトを特定します。  
  
    1.  **[プロジェクト名]**: Integration Services プロジェクトは "Package.DQS Cleansing_*\<日付>**\<時刻>*_{GUID}" の名前付け規則を使用して表示されます。 同じパッケージを [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で正常に実行するたびに、新しいプロジェクトが **[プロジェクトを開く]** 画面に表示されます。  
  
    2.  **[プロジェクトの種類]**: Integration Services プロジェクトはプロジェクトの種類が **[SSIS]** として **[プロジェクトを開く]** 画面に表示されます。  
  
     プロジェクトを選択して **[次へ]** をクリックします。  
  
4.  Integration Services プロジェクトが、インタラクティブなクレンジング ステージとして (**[管理ビューと結果]** タブで) 開きます。 Integration Services プロジェクト内のデータに対してインタラクティブなクレンジングを実行できます。 **[結果の管理と表示]** タブについて詳しくは、「[DQS &#40;内部&#41; ナレッジを使用したデータのクレンジング](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md)」の「[インタラクティブなクレンジング ステージ](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md#Interactive)」をご覧ください。  
  
5.  **[次へ]** をクリックして **[エクスポート]** タブに進みます。ここでは処理されたデータを、SQL Server データベースの新しいテーブル、.csv ファイル、または Excel ファイルにエクスポートできます。 **[エクスポート]** タブについて詳しくは、「[DQS &#40;内部&#41; ナレッジを使用したデータのクレンジング](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md)」の「[エクスポート ステージ](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md#Export)」をご覧ください。  
  
6.  データをエクスポートした後で **[完了]** をクリックして Integration Services プロジェクトを閉じます。  
  
 ![上部のリンクに戻る で使用される矢印アイコン](../2014-toc/media/uparrow16x16.gif "に戻る リンクの上位で使用される矢印アイコン")[でこのトピック](#Intro)  
  
## <a name="see-also"></a>参照  
 [DQS クレンジング変換](../integration-services/data-flow/transformations/dqs-cleansing-transformation.md)   
 [Integration Services &#40;SSIS&#41;プロジェクト](../integration-services/integration-services-ssis-projects-and-solutions.md)  
  
  
