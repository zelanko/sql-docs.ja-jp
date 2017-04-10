---
title: "SQL Server Data Tools でのパッケージのコピー | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "パッケージ [Integration Services], コピー"
  - "パッケージのコピー"
  - "パッケージの GUID の再生成"
  - "パッケージのプロパティの更新"
ms.assetid: 03edc659-e76d-48c0-a749-5f1899b6b507
caps.latest.revision: 18
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 18
---
# SQL Server Data Tools でのパッケージのコピー
  このトピックでは、既存のパッケージをコピーして新しい [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージを作成する方法、および新しいパッケージの **Name** プロパティと **GUID** プロパティを更新する方法について説明します。  
  
### パッケージをコピーするには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] で、コピーするパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。  
  
2.  ソリューション エクスプローラーで、パッケージをダブルクリックします。  
  
3.  コピーするパッケージがソリューション エクスプローラーで選択されていること、またはパッケージが含まれている SSIS デザイナーのタブがアクティブになっていることを確認します。  
  
4.  **[ファイル]** メニューの **[名前を付けて \<パッケージ名> を保存]** をクリックします。  
  
    > [!NOTE]  
    >  **[ファイル]** メニューに **[名前を付けて保存]** オプションを表示するには、SSIS デザイナーでパッケージを開いておく必要があります。  
  
5.  必要に応じて、別のフォルダーを参照します。  
  
6.  パッケージ ファイルの名前を更新します。 ファイル拡張子は、必ず .dtsx のままにしておきます。  
  
7.  **[保存]**をクリックします。  
  
8.  プロンプトで、パッケージ オブジェクトの名前をファイル名と一致するように更新するかどうかを選択します。 **[はい]** をクリックすると、パッケージの **Name** プロパティが更新されます。 新しいパッケージが [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトに追加され、[!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーで開かれます。  
  
9. 必要に応じて、**[制御フロー]** タブの背景をクリックし、**[プロパティ]** をクリックします。  
  
10. [プロパティ] ウィンドウで、ID プロパティの値をクリックし、ボックスの一覧の **[\<新しい ID の生成>]** をクリックします。  
  
11. **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックし、新しいパッケージを保存します。  
  
## 参照  
 [パッケージのコピーを保存する](../Topic/Save%20a%20Copy%20of%20a%20Package.md)   
 [SQL Server データ ツールでのパッケージの作成](../integration-services/create-packages-in-sql-server-data-tools.md)   
 [Integration Services (SSIS) パッケージ](../integration-services/integration-services-ssis-packages.md)  
  
  