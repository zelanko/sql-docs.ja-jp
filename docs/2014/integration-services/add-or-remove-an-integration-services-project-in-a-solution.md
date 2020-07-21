---
title: ソリューション内の Integration Services プロジェクトを追加または削除する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- adding projects
- Integration Services projects, adding
- SQL Server Integration Services projects, adding
- SSIS projects, adding
- projects [Integration Services], adding
ms.assetid: f01f6475-b63c-41dc-82ac-b62162b3adf7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 29f64f915f241ec274cf4a7babdf9937fe6c4131
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85439629"
---
# <a name="add-or-remove-an-integration-services-project-in-a-solution"></a>ソリューション内の Integration Services プロジェクトを追加または削除する
  ソリューション内の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを追加または削除する手順を次に示します。  
  
 プロジェクトを既存のソリューションに追加したり、既存のソリューションから削除したりできるのは、そのソリューションが [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] で表示されている場合のみです。 で [**常にソリューションを表示**] オプションを選択した場合 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ソリューションに含まれるプロジェクトが1つしかない場合でも、によってソリューションが表示されます。 このオプションを選択していない場合は、ソリューションに 2 つ以上のプロジェクトが含まれているときに限り、[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] でソリューションが表示されます。 その他のプロジェクトは、[!INCLUDE[ssIS](../includes/ssis-md.md)] プロジェクトでも他の種類のプロジェクトでもかまいません。  
  
## <a name="adding-an-integration-services-project"></a>Integration Services プロジェクトの追加  
 プロジェクトを追加する場合は、[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] で新しい空のプロジェクトを作成することも、別のソリューション用に既に作成したプロジェクトを追加することもできます。 プロジェクトを既存のソリューションに追加できるのは、そのソリューションが [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] で表示されている場合のみです。  
  
#### <a name="to-add-a-new-integration-services-project-to-a-solution"></a>新しい Integration Services プロジェクトをソリューションに追加するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] で、新しい [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトの追加先となるソリューションを開き、次のいずれかの操作を行います。  
  
    -   ソリューションを右クリックして **[追加]** をクリックし、**[新しいプロジェクト]** をクリックします。  
  
    -   **[ファイル]** メニューの **[追加]** をポイントし、**[新しいプロジェクト]** をクリックします。  
  
2.  **[新しいプロジェクトの追加]** ダイアログ ボックスの **[テンプレート]** ペインで、**[Integration Services プロジェクト]** をクリックします。  
  
3.  必要に応じて、プロジェクトの名前と場所を変更します。  
  
4.  **[OK]** をクリックします。  
  
#### <a name="to-add-an-existing-integration-services-project-to-a-solution"></a>既存の Integration Services プロジェクトをソリューションに追加するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] で、既存の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを追加するソリューションを開き、次のいずれかの操作を行います。  
  
    -   ソリューションを右クリックして **[追加]** をポイントし、**[既存のプロジェクト]** をクリックします。  
  
    -   **[ファイル]** メニューの **[追加]** をクリックし、**[既存のプロジェクト]** をクリックします。  
  
2.  **[既存プロジェクトの追加]** ダイアログ ボックスで、追加するプロジェクトを選択して、**[開く]** をクリックします。  
  
3.  選択したプロジェクトが、**ソリューション エクスプローラー**のソリューション フォルダーに追加されます。  
  
## <a name="removing-an-integration-services-project"></a>Integration Services プロジェクトの削除  
 プロジェクトをソリューションから削除できるのは、そのソリューションが [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] で表示されている場合のみです。 ソリューションが表示されていれば、1 つのプロジェクト以外はすべて削除できます。 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] では、残りのプロジェクトが 1 つのみになった時点でソリューション フォルダーが表示されなくなるので、最後の 1 つのプロジェクトは削除できません。  
  
#### <a name="to-remove-an-integration-services-project-from-a-solution"></a>Integration Services プロジェクトをソリューションから削除するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] で、[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを削除する対象となるソリューションを開きます。  
  
2.  ソリューション エクスプローラーでプロジェクトを右クリックし、**[プロジェクトのアンロード]** をクリックします。  
  
3.  削除を確認するメッセージが表示されたら、**[OK]** をクリックします。  
  
## <a name="see-also"></a>関連項目  
 [SSIS&#41; プロジェクトの Integration Services &#40;](integration-services-ssis-projects-and-solutions.md)   
 [新しい Integration Services プロジェクトを作成する](../../2014/integration-services/create-a-new-integration-services-project.md)  
  
  
