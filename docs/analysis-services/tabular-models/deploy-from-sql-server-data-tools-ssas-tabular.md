---
title: "SQL Server データ ツールからの配置 (SSAS テーブル) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.asvs.bidtoolset.deploystatus.f1"
ms.assetid: 67dde3fe-ba43-41f3-b56c-c656029ee93f
caps.latest.revision: 17
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 17
---
# SQL Server データ ツールからの配置 (SSAS テーブル)
  このトピックのタスクは、[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] の Deploy コマンドを使用してテーブル モデル ソリューションを配置するために使用します。  
  
 このトピックのセクション:  
  
-   [配置オプションおよび配置サーバー プロパティの構成](#bkmk_deploy)  
  
-   [テーブル モデル ソリューションの配置](#bkmk_deploy_proc)  
  
-   [配置状態](#bkmk_deploy_status)  
  
##  <a name="bkmk_deploy"></a> 配置オプションおよび配置サーバー プロパティの構成  
 テーブル モデル ソリューションを配置する前に、まず、配置オプションと配置サーバーのプロパティを指定する必要があります。 配置のプロパティおよび設定の詳細については、「[テーブル モデル ソリューションの配置 (SSAS テーブル)](../../analysis-services/tabular-models/tabular-model-solution-deployment-ssas-tabular.md)」を参照してください。  
  
#### 配置オプションおよび配置サーバー プロパティを構成するには  
  
1.  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] の**ソリューション エクスプローラー**で、プロジェクト名を右クリックして、**[プロパティ]** をクリックします。  
  
2.  **[\<project name> のプロパティ]** ダイアログ ボックスの **[配置オプション]** で、プロパティの設定を指定します (既定の設定と異なる場合)。  
  
    > [!NOTE]  
    >  キャッシュ モードのモデルの場合、**[クエリ モード]** は常に **[In-Memory]** です。  
  
    > [!NOTE]  
    >  DirectQuery モードのモデルの場合、**[権限借用設定]** は指定できません。  
  
3.  **[配置サーバー]** で、**[サーバー]** (名前)、**[エディション]**、**[データベース]** (名前)、**[キューブ名]** の各プロパティの設定を指定し (既定の設定と異なる場合)、**[OK]** をクリックします。  
  
> [!NOTE]  
>  作成した新しいプロジェクトが指定したサーバーに自動的に配置されるように、既定の配置サーバー プロパティの設定を指定することもできます。 詳細については、「[既定のデータ モデルと配置プロパティの構成 (SSAS テーブル)](../../analysis-services/tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md)」を参照してください。  
  
##  <a name="bkmk_deploy_proc"></a> テーブル モデル ソリューションの配置  
  
#### テーブル モデル ソリューションを配置するには  
  
-   [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] で、**[ビルド]** メニューの **[\<project name> の配置]** をクリックします。  
  
     **[配置]** ダイアログ ボックスが表示され、メタデータの配置の状態とモデルに含まれる各テーブルの処理が示されます ([処理オプション] プロパティが [処理しない] に設定されている場合を除きます)。 配置プロセスが完了したら、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、Analysis Services インスタンスに接続し、新しい model データベース オブジェクトが作成されていることを確認するか、クライアント レポート アプリケーションを使用して配置済みモデルと接続します。  
  
##  <a name="bkmk_deploy_status"></a> 配置状態  
 **[配置]** ダイアログ ボックスでは、配置操作の進行状況を監視できます。 配置操作を停止することもできます。  
  
 **[状態]**  
 配置操作が正常に行われたかどうかを示します。  
  
 **詳細**  
 配置されたメタデータ項目と各メタデータ項目の状態を一覧表示し、何か問題があればメッセージを表示します。  
  
 **[展開の停止]**  
 クリックすると、配置操作が停止されます。 このオプションは、配置操作に時間がかかりすぎる場合や、エラーが多すぎる場合に有効です。  
  
## 参照  
 [テーブル モデル ソリューションの配置 (SSAS テーブル)](../../analysis-services/tabular-models/tabular-model-solution-deployment-ssas-tabular.md)   
 [既定のデータ モデルと配置プロパティの構成 (SSAS テーブル)](../../analysis-services/tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md)  
  
  