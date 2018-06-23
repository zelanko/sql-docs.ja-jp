---
title: クレンジングと照合のしきい値の構成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dqs.admin.config.general.f1
helpviewer_keywords:
- cleansing,threshold value
- cleansing threshold values
- matching,threshold value
ms.assetid: d2305409-7115-45a4-8f60-1213c0a47368
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 19425baf1fcf1f3fef0a4cf630242d8b16a35f9e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36076643"
---
# <a name="configure-threshold-values-for-cleansing-and-matching"></a>クレンジングと照合のしきい値の構成
  このトピックでは、コンピューター支援型のクレンジングおよび照合アクティビティの最中に [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) で使用されるしきい値を構成する方法について説明します。  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 これらのしきい値を構成するには、DQS_MAIN データベースの dqs_administrator ロールが必要です。  
  
##  <a name="Configure"></a> しきい値の構成  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]「[Data Quality Client アプリケーションの実行](../../2014/data-quality-services/run-the-data-quality-client-application.md)」をご覧ください。  
  
2.  [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] のホーム画面で **[構成]** をクリックします。  
  
3.  次に **[全般設定]** タブをクリックします。このタブではクレンジングと照合アクティビティのしきい値を指定できます。  
  
4.  クレンジング アクティビティのしきい値を指定するには、 **[インタラクティブなクレンジング]** の下の次のボックスに適切な値を指定します。  
  
    -   **[提案の最小スコア]**: コンピューター支援型のクレンジング プロセスの最中に、値の変更を提案するために DQS によって使用される最小スコア (信頼レベル) です。 割合値に相当する値を 10 進数表記で入力します。 たとえば、75% であれば「0.75」と入力します。 この値は **[自動修正の最小スコア]** ボックスに指定した値以下である必要があります。 既定値は 0.7 です。  
  
    -   **[自動修正の最小スコア]**: コンピューター支援型のクレンジング プロセスの最中に、値を自動修正するために DQS によって使用される最小スコア (信頼レベル) です。 割合値に相当する値を 10 進数表記で入力します。 たとえば、90% であれば「0.9」と入力します。 既定値は 0.8 です。  
  
5.  照合アクティビティのしきい値を指定するには、 **[照合]** の下の **[最小レコード スコア]** ボックスに適切な値を指定します。 この値は、あるレコードが別のレコードと一致すると見なされる最小スコアを表します。 既定値は 80% です。  
  
6.  **[閉じる]** をクリックします。  
  
  