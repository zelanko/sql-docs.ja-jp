---
title: "保存されている構成ファイルを使用してログ記録を構成する | Microsoft Docs"
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
  - "コンテナー [Integration Services], ログ"
  - "ログ [Integration Services], コンテナー"
ms.assetid: e5fdbbcb-94ca-4912-aa7c-0d89cebbd308
caps.latest.revision: 42
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 42
---
# 保存されている構成ファイルを使用してログ記録を構成する
  この手順では、以前に保存したログ構成ファイルを読み込んでパッケージ内の新しいコンテナーのログ記録を構成する方法について説明します。  
  
 既定では、パッケージに含まれるすべてのコンテナーは、親コンテナーと同じログ構成を使用します。 たとえば、Foreach ループ内のタスクは、Foreach ループと同じログ構成を使用します。  
  
### コンテナーのログ記録を構成するには  
  
1.  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトを開きます。  
  
2.  次に、 **[SSIS]** メニューの **[ログ記録]**をクリックします。  
  
3.  パッケージ ツリー ビューを展開し、構成するコンテナーを選択します。  
  
4.  **[プロバイダーとログ]** タブで、コンテナーに対して使用するログを選択します。  
  
    > [!NOTE]  
    >  ログは、パッケージ レベルでのみ作成できます。 詳しくは、「[SQL Server Data Tools でパッケージのログ記録を有効にする](../../integration-services/performance/enable-package-logging-in-sql-server-data-tools.md)」をご覧ください。  
  
5.  **[詳細]** タブをクリックし、**[読み込み]** をクリックします。  
  
6.  使用するログ構成ファイルを参照し、**[開く]** をクリックします。  
  
7.  必要に応じて、**[イベント]** 列のチェック ボックスをオンにして、ログ記録を行う異なるログ エントリを選択することもできます。 **[詳細設定]** をクリックして、このエントリのログ記録を行うための情報の種類を選択します。  
  
    > [!NOTE]  
    >  最初にログ構成を作成するときに使用されたコンテナーでは使用できない追加のログ エントリが新しいコンテナーに含まれている場合があります。 これらの追加のログ エントリをログに記録するには、手動で選択する必要があります。  
  
8.  **[保存]** をクリックして、ログ構成の更新バージョンを保存します。  
  
9. 更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。  
  
## 参照  
 [Integration Services &#40;SSIS&#41; のログ記録](../../integration-services/performance/integration-services-ssis-logging.md)  
  
  