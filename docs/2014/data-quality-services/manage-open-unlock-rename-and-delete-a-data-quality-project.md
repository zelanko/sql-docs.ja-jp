---
title: 管理 (開く、ロック解除、名前の変更、および削除)、データ品質プロジェクト |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.dqproject.opendqproject.f1
helpviewer_keywords:
- data quality project,delete
- data quality project,rename
- data quality project,unlock
- data quality project,open
ms.assetid: de8a2b04-4673-4beb-b4cf-96a28cdf3a93
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 53d89072b28527a21c71373b905455426d4c664c
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2018
ms.locfileid: "52535444"
---
# <a name="manage-open-unlock-rename-and-delete-a-data-quality-project"></a>データ品質プロジェクトの管理 (開く、ロック解除、名前の変更、および削除)
  このトピックでは、データ品質プロジェクトを開く、ロック解除、名前の変更、削除などの、 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] を使用したデータ品質プロジェクトの管理方法について説明します。  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="LimitationsRestrictions"></a> 制限事項と制約事項  
  
-   他のユーザーによって作成された、ロックされているプロジェクトは開くことができません。  
  
-   他のユーザーによって作成されたデータ品質プロジェクトのロック解除、名前の変更、または削除はできません。  
  
-   ロックされたデータ品質プロジェクトを削除することはできません。 削除するには先にロックを解除する必要があります。  
  
-   自分が作成したデータ品質プロジェクトのみロックを解除することができます。  
  
###  <a name="Prerequisites"></a> 前提条件  
 管理対象のデータ品質プロジェクトが少なくとも 1 つ必要です。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 データ品質プロジェクトを管理するには、DQS_MAIN データベースに対する dqs_kb_editor または dqs_kb_operator ロールが必要です。  
  
##  <a name="Open"></a> データ品質プロジェクトを開く  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]「[Data Quality Client アプリケーションの実行](../../2014/data-quality-services/run-the-data-quality-client-application.md)」をご覧ください。  
  
2.  [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] のホーム画面で、 **[データ品質プロジェクトを開く]** をクリックします。 **[プロジェクトを開く]** 画面が表示されます。  
  
     または、 **[最近使用したデータ品質プロジェクト]** 領域の下に表示されるデータ品質プロジェクトをクリックして直接開くこともできます。  
  
3.  **[プロジェクトを開く]** 画面で、開きたいデータ品質プロジェクトをクリックして選択し、 **[次へ]** をクリックします。  
  
4.  最後に閉じられたときと同じアクティビティの状態でデータ品質プロジェクトが開きます。 データ品質プロジェクトには次の状態があります。  
  
    -   **クレンジング**アクティビティ、データ品質プロジェクトは、次の状態であることができます。**クレンジング - マップ**、**クレンジング - クレンジング**、**クレンジング - 管理し、結果を表示**、および**クレンジング - エクスポート**します。  
  
    -   **照合**アクティビティ、データ品質プロジェクトは、次の状態であることができます。**照合 - マップ**、**照合 - 照合**、**照合 - サバイバーシップ**、および**照合 - エクスポート**します。  
  
##  <a name="Unlock"></a> データ品質プロジェクトのロック解除  
 データ品質プロジェクトを作成すると、プロジェクトは他のユーザーによる使用や変更を防ぐためにロック状態になります。 他のユーザーがデータ品質プロジェクトを操作できるようにするには、作業を完了した後にデータ品質プロジェクトのロックを解除する必要があります。 ロックされているプロジェクトには、ロック アイコンが表示されます。  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]「[Data Quality Client アプリケーションの実行](../../2014/data-quality-services/run-the-data-quality-client-application.md)」をご覧ください。  
  
2.  [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] のホーム画面で、 **[データ品質プロジェクトを開く]** をクリックします。 **[プロジェクトを開く]** 画面が表示されます。  
  
3.  **[プロジェクトを開く]** 画面で、自分が作成したロックされているデータ品質プロジェクトを右クリックし、ショートカット メニューの **[ロック解除]** をクリックします。 緑のチェック マークがプロジェクトに表示され、ロックされていないことが示されます。  
  
##  <a name="Rename"></a> データ品質プロジェクトの名前の変更  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]「[Data Quality Client アプリケーションの実行](../../2014/data-quality-services/run-the-data-quality-client-application.md)」をご覧ください。  
  
2.  [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] のホーム画面で、 **[データ品質プロジェクトを開く]** をクリックします。 **[プロジェクトを開く]** 画面が表示されます。  
  
3.  **[プロジェクトを開く]** 画面で、自分が作成したデータ品質プロジェクトを右クリックし、ショートカット メニューの **[名前の変更]** をクリックします。  
  
4.  **[名前]** 列のデータ品質プロジェクト名が編集可能になります。 新しい名前を入力して、Enter キーを押します。  
  
##  <a name="Delete"></a> データ品質プロジェクトの削除  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]「[Data Quality Client アプリケーションの実行](../../2014/data-quality-services/run-the-data-quality-client-application.md)」をご覧ください。  
  
2.  [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] のホーム画面で、 **[データ品質プロジェクトを開く]** をクリックします。 **[プロジェクトを開く]** 画面が表示されます。  
  
3.  **[プロジェクトを開く]** 画面で、自分が作成したロックされていないデータ品質プロジェクトを右クリックし、ショートカット メニューの **[削除]** をクリックします。  
  
4.  確認のメッセージが表示されます。 **[はい]** をクリックします。  
  
  
