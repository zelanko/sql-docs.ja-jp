---
title: データ品質プロジェクトの作成 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology:
- data-quality-services
ms.topic: conceptual
f1_keywords:
- sql13.dqs.dqproject.newdqproject.f1
helpviewer_keywords:
- create,data quality project
- data quality project,create
ms.assetid: 19c52d2b-d28e-4449-ab59-5fe0dc326cd9
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 213de190546d58b16a13e226b4f2e08737b8ce31
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47787226"
---
# <a name="create-a-data-quality-project"></a>データ品質プロジェクトの作成

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  このトピックでは、 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]を使用してデータ品質プロジェクトを作成する方法について説明します。 データ品質プロジェクトは、 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) でクレンジングおよび照合アクティビティの実行に使用されます。  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Prerequisites"></a> 前提条件  
 データ品質プロジェジェクトでクレンジングおよび照合アクティビティに使用する関連のナレッジ ベースが必要です。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 データ品質プロジェクトを作成するには、DQS_MAIN データベースに対する dqs_kb_editor または dqs_kb_operator ロールが必要です。  
  
##  <a name="Create"></a> データ品質プロジェクトの作成  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]「[Data Quality Client アプリケーションの実行](../data-quality-services/run-the-data-quality-client-application.md)」をご覧ください。  
  
2.  [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] ホーム画面で、 **[新しいデータ品質プロジェクト]** をクリックします。  
  
3.  **[新しいデータ品質プロジェクト]** 画面で、次の手順を実行します。  
  
    1.  **[名前]** ボックスに新しいデータ品質プロジェクトの名前を入力します。  
  
    2.  (省略可能) **[説明]** ボックスに新しいデータ品質プロジェクトの説明を入力します。  
  
    3.  **[ナレッジ ベースを使用する]** ボックスの一覧で、データ品質プロジェクトに使用するナレッジ ベースを選択します。 右側にある **[ナレッジ ベースの詳細: <ナレッジ ベース名>]** 領域に、選択したナレッジ ベースで使用可能なドメイン名が表示されます。  
  
    4.  **[アクティビティの選択]** 領域で、このデータ品質プロジェクトを使用して実行するアクティビティをクリックします。  
  
        -   **[クレンジング]**: ソース データをクレンジングするには、このアクティビティを選択します。  
  
        -   **[照合]**: 照合を実行するには、このアクティビティを選択します。 このアクティビティは、データ品質プロジェクトで選択されたナレッジ ベースに照合ポリシーが含まれている場合にのみ利用可能です。  
  
4.  **[作成]** をクリックし、データ品質プロジェクトを作成します。  
  
##  <a name="FollowUp"></a> 補足情報: データ品質プロジェクトを作成した後  
 データ品質プロジェクトを作成した後に、選択したアクティビティ (クレンジングと照合) の実行に使用するウィザードが示されます。 クレンジングと照合アクティビティについて詳しくは、「[データ クレンジング](../data-quality-services/data-cleansing.md)」および「[データ照合](../data-quality-services/data-matching.md)」をご覧ください。  
  
  
