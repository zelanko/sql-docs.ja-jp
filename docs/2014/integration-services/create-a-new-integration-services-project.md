---
title: 新しい Integration Services プロジェクトを作成 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects [Integration Services], creating
- Integration Services projects, creating
- SQL Server Integration Services projects, creating
- SSIS projects, creating
ms.assetid: 1e23f259-0401-4333-ab4f-89809aae63b1
caps.latest.revision: 51
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 4ee4484b97102b6bae3bd9496ee161233c47ee12
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36073286"
---
# <a name="create-a-new-integration-services-project"></a>新しい Integration Services プロジェクトを作成する
  この手順では、新しいプロジェクトと新しい [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ソリューションを作成します。  
  
### <a name="to-create-a-new-integration-services-project"></a>新しい Integration Services プロジェクトを作成するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]を開きます。  
  
2.  **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。  
  
3.  **[新しいプロジェクト]** ダイアログ ボックスの **[テンプレート]** ペインで、**[Integration Services プロジェクト]** テンプレートを選択します。  
  
     **[Integration Services プロジェクト]** テンプレートでは、空のパッケージを 1 つ含む [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトが作成されます。  
  
4.  (省略可) プロジェクトの名前と場所を変更します。  
  
     ソリューション名は、プロジェクト名と一致するように自動的に更新されます。  
  
5.  ソリューション ファイル用に別のフォルダーを作成するには、**[ソリューションのディレクトリを作成]** を選択します。 既定のオプションです。  
  
6.  ソース管理ソフトウェアがコンピューターにインストールされている場合、プロジェクトをソース管理に関連付けるには、**[ソース管理に追加]** を選択します。  
  
7.  ソース管理ソフトウェアが [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe の場合、**[Visual SourceSafe ログイン]** ダイアログ ボックスが開きます。 **[Visual SourceSafe ログイン]** ダイアログ ボックスで、ユーザー名、パスワード、および [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe データベースの名前を指定します。 データベースを探すには、**[参照]** をクリックします。  
  
    > [!NOTE]  
    >  選択したソース管理プラグインを表示、変更したり、ソース管理の環境を構成するには、**[ツール]** メニューの **[オプション]** をクリックし、**[ソース管理]** ノードを展開します。  
  
8.  をクリックして **[ok]** をソリューションに追加**ソリューション エクスプ ローラー**r し、ソリューションにプロジェクトを追加します。  
  
## <a name="see-also"></a>参照  
 [Integration Services &#40;SSIS&#41;プロジェクト](integration-services-ssis-projects-and-solutions.md)   
 [ソリューション内の Integration Services プロジェクトを追加または削除する](../../2014/integration-services/add-or-remove-an-integration-services-project-in-a-solution.md)  
  
  