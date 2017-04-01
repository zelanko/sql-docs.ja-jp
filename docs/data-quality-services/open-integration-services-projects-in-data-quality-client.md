---
title: "Data Quality Client で Integration Services プロジェクトを開く | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a8bad2f1-8fb0-4d14-a978-11a5720e62d6
caps.latest.revision: 9
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 9
---
# Data Quality Client で Integration Services プロジェクトを開く
  Integration Services の DQs クレンジング コンポーネントでは、クレンジング プロジェクトをバッチ モードで実行することができます。 ただし、時々 たいでクレンジング結果を確認する方法のような Integration Services パッケージでクレンジング結果を確認、 **管理と結果を表示する** DQS でデータ品質プロジェクトでクレンジング アクティビティのタブをクリックします。 DQS では、[Integration Services プロジェクトを開いたりすることができます [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] から他のデータ品質プロジェクトと同じように、 **プロジェクトを開く** 画面で、Integration Services プロジェクトでクレンジング結果のインタラクティブなクレンジング経験があるとします。  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="LimitationsRestrictions"></a> 制限事項と制約事項  
  
-   完了した Integration Services プロジェクトで使用できる専用、 **プロジェクトを開く** 画面で [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]します。 実行中かどうかのプロジェクトでは使用できない、 **プロジェクトを開く** 画面です。  
  
-   インタラクティブなクレンジング ステージで integration Services プロジェクトを開きます (**管理ビューと結果** ] タブ) で [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]します。 アクセスできない、 **整備** または **マップ** タブです。 だけ移動できます、 **エクスポート** ] タブをクリックして **次**します。  
  
-   ロックされた Integration Services プロジェクトを [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] から削除することはできません。 削除するには先にロックを解除する必要があります。  
  
###  <a name="Prerequisites"></a> 前提条件  
 必要が正常に完了するには、表示して開くために DQS クレンジング コンポーネントを使用してパッケージを含む Integration Services プロジェクトを実行する [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]です。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 Integration Services プロジェクトを開くためには、DQS_MAIN データベースに対する dqs_kb_editor または dqs_kb_operator ロールが必要です。  
  
  
##  <a name="Open"></a> Integration Services プロジェクトを開く  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Data Quality Client アプリケーションを実行](../data-quality-services/run-the-data-quality-client-application.md)します。  
  
2.   [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] ホーム画面で、[ **データ品質プロジェクトを開く**します。 **[プロジェクトを開く]** 画面が表示されます。  
  
3.   **プロジェクトを開く** ] 画面で、次の方法のいずれかで Integration Services プロジェクトを識別できます。  
  
    1.  **プロジェクト名**: Integration Services プロジェクトでは、次の名前付けの用語を使用して一覧表示されます:"Package.DQS cleansing _*\< 日付>**\< 時間>*_ {GUID}"。 同じパッケージを正常に実行するたびに [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], で新しいプロジェクトが表示されている、 **プロジェクトを開く** 画面です。  
  
    2.  **プロジェクトの種類が**: Integration Services プロジェクトがある **SSIS** プロジェクトの種類として、 **プロジェクトを開く** 画面です。  
  
     プロジェクトを選択し、クリックして **次**します。  
  
4.  インタラクティブなクレンジング ステージで Integration Services プロジェクトを開きます (**管理ビューと結果** ] タブ)。 Integration Services プロジェクト内のデータに対してインタラクティブなクレンジングを実行できます。 詳細については、 **管理と結果を表示する** ] タブを参照してください [インタラクティブなクレンジング ステージ](../data-quality-services/cleanse-data-using-dqs-internal-knowledge.md#Interactive) で [データを使用して DQS のクレンジング &#40";"内部"&"#41 です。ナレッジ](../data-quality-services/cleanse-data-using-dqs-internal-knowledge.md)します。  
  
5.  をクリックして **次** に行き、 **エクスポート** ] タブをクリックすると、次のいずれかの処理後のデータのエクスポート先となる: SQL Server データベース、.csv ファイルまたは Excel ファイルの新しいテーブル。 詳細については、 **エクスポート** ] タブを参照してください [エクスポート ステージ](../data-quality-services/cleanse-data-using-dqs-internal-knowledge.md#Export) で [データを使用して DQS のクレンジング &#40";"内部"&"#41 です。ナレッジ](../data-quality-services/cleanse-data-using-dqs-internal-knowledge.md)  
  
6.  クリックして、データをエクスポートしたら **完了** Integration Services プロジェクトを閉じます。  

  
## 参照  
 [DQS クレンジング変換](../integration-services/data-flow/transformations/dqs-cleansing-transformation.md)   
 [Integration Services (SSIS) プロジェクト](https://msdn.microsoft.com/library/ms138028.aspx)  
  
  