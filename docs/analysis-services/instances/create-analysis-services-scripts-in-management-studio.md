---
title: "Management Studio での Analysis Services スクリプトの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/06/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Analysis Services オブジェクト, スクリプト"
  - "オブジェクト [Analysis Services], スクリプト"
  - "スクリプト [Analysis Services], オブジェクト"
ms.assetid: 4f1b965c-9ca6-427b-8f4d-0ce1eea7c0fe
caps.latest.revision: 36
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 36
---
# Management Studio での Analysis Services スクリプトの作成
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] には、スクリプトの生成機能、テンプレート、および Analysis Services オブジェクトとタスクのスクリプトを作成するために使用できるエディターが含まれています。  
  
## Management Studio で Analysis Services タスクのスクリプトを作成する  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のタスクのスクリプト作成は、タスク指向のダイアログ ボックスで、いずれかのスクリプト オプションをクリックすることで実現します。 バックアップやデータベースの復元、オブジェクトの処理、集計のデザインなどのタスクを実行するために使用するすべてのダイアログ ボックスには、ダイアログ ボックスの上部にスクリプト オプションがあります。 これらのオプションのいずれかを選択すると、ダイアログ ボックス内の情報と設定に基づいて、XMLA スクリプトが生成されます。  
  
 既定では、スクリプトが生成され、XMLA クエリ エディター内に配置されますが、スクリプト オプション リストを拡張して、Windows クリップボードやファイルにスクリプトを出力することもできます。  
  
#### Analysis Services タスクのスクリプトを作成するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスに接続します。  
  
2.  データベースを右クリックし、**[バックアップ]** をクリックします。 [データベースのバックアップ] ダイアログ ボックスが開きます。 バックアップのファイル名を指定し、このバックアップに必要なオプションを選択します。  
  
3.  ダイアログ ボックスの上部にある **[スクリプト]** をクリックします。 スクリプト機能は、Management Studio 内のすべてのタスク ベースのダイアログ ボックスに含まれています。 これには、次のオプションがあります。**[スクリプト操作を新規クエリ ウィンドウに保存]** は、クエリ エディター ウィンドウを開き、**[スクリプト操作をファイルに保存]** は、XMLA スクリプトをファイルに保存し、**[スクリプト操作をクリップボードに保存]** は、XMLA スクリプトをクリップボードに保存します。  
  
     Management Studio でスクリプト オプションとして表示される **[スクリプト操作をジョブに保存]** オプションは、Analysis Services スクリプトではサポートされていないことに注意してください。  
  
4.  既定のオプションである **[スクリプト操作を新規クエリ ウィンドウに保存]** を選択すると、生成されたスクリプトは、XMLA クエリ ウィンドウに配置されます。  
  
     [データベースのバックアップ] ダイアログ ボックスを閉じて、XMLA スクリプトを直接、編集または実行できます。  
  
## Management Studio で Analysis Services オブジェクトのスクリプトを作成する  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] では、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] オブジェクトを右クリックし、**[CREATE]**、**[ALTER]**、または **[DELETE]** を選択して、オブジェクトのスクリプト作成を実行します。 これらの各オプションは、ウィンドウまたはファイルに出力できますが、スクリプトの出力先に関係なく、XMLA ラッパーの DDL スクリプトの形式で出力されます。 このようなスクリプトは、指定するどのサーバーに対しても実行できるという大きな利点があります。 また、スクリプトの名前は変更可能で、オブジェクトの大量作成、変更、または削除を反復的に行うことができます。  
  
 スクリプトを作成できるオブジェクトには、データ ソース、データ ソース ビュー、キューブ、ディメンション、マイニング構造、およびロールを含む [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースの要素が含まれます。  
  
 前提条件として XML for Analysis (XMLA) を理解している必要があります。 しかし、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] には、キューブなどのオブジェクトの作成に必要な XMLA スクリプトを自動的に作成する機能があります。 この自動化機能により、XMLA の習得の必要性が緩和されます。 XMLA の使用方法の詳細については、「[Analysis Services での XMLA による開発](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)」を参照してください。 XMLA の使用方法の詳細については、「[Analysis Services での XMLA による開発](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)」を参照してください。  
  
> [!IMPORTANT]  
>  Role オブジェクトのスクリプトを作成する場合、セキュリティ権限はオブジェクトが関連付けられているセキュリティ ロールではなく、オブジェクト自体に含まれていることに注意してください。  
  
#### Analysis Services オブジェクトのスクリプトを作成するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスに接続します。  
  
2.  オブジェクトの作成、変更、削除のいずれかを行うスクリプトを作成するオブジェクトを選択します。  
  
3.  オブジェクトを右クリックし、**[キューブをスクリプト化]** をポイントしてから、**[CREATE]**、**[ALTER]**、**[DELETE]** のいずれかをポイントし、クエリ エディター ウィンドウを開くには **[新しいクエリ エディター ウィンドウ]** を、XMLA スクリプトをファイルに保存するには **[ファイル]** を、XMLA スクリプトをクリップボードに保存するには **[クリップボード]** をクリックします。  
  
    > [!NOTE]  
    >  通常、複数の異なるバージョンのファイルを作成する場合は、**[ファイル]** を選択します。  
  
## 参照  
 [Analysis Services の管理タスクのスクリプト作成](../../analysis-services/instances/script-administrative-tasks-in-analysis-services.md)   
 [XMLA クエリ エディター (Analysis Services - 多次元データ)](../Topic/XMLA%20Query%20Editor%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)  
  
  