---
title: ソース管理にプロジェクトの追加 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- adding projects
- projects [SQL Server Management Studio], adding
ms.assetid: fd4616b2-a564-4a66-ac53-d1f5cba213c2
caps.latest.revision: 27
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9507be8eb78f84ddb775a70a997813166a06d08c
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2018
ms.locfileid: "43815778"
---
# <a name="add-projects-to-source-control"></a>ソース管理へのプロジェクトの追加
  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ソリューションには、複数のスクリプト プロジェクトを含めることができます。 ソース管理にプロジェクトを追加する方法は、そのプロジェクトが属しているソリューションがソース管理の下にあるかどうかによって異なります。 ソリューションがソース管理の対象である場合は、ソリューションをチェックインすると、ソース管理にプロジェクトが自動的に追加されます。 ソリューションのチェックインの詳細については、次を参照してください。[ファイルで確認](../../2014/database-engine/check-in-files.md)します。  
  
 対象のプロジェクトが属しているソリューションがソース管理の対象でない場合は、ソリューションをソース管理に追加すると、ソリューションのプロジェクトが自動的に追加されます。 ソース管理にソリューションを追加する方法の詳細については、次を参照してください。[ソリューションをソース コントロールに追加](../../2014/database-engine/add-solutions-to-source-control.md)します。  
  
 使用することができます、ソリューションをソース管理に追加したくない場合、**をソース管理に追加選択**プロジェクトを手動で追加するコマンド。  
  
 データベース オブジェクトはソース管理プロバイダーによって直接保護されませんが、データベース オブジェクトのスクリプトを作成し、そのスクリプトをソース管理の下で保存することができます。  
  
### <a name="to-add-a-project-to-source-control"></a>ソース管理にプロジェクトを追加するには  
  
1.  ソリューション エクスプローラーで、プロジェクトを選択します。  
  
2.  **ファイル**メニューで、**ソース管理**、] をクリックし、 **[選択されたプロジェクトをソース管理に追加**します。  
  
    > [!NOTE]  
    >  使用する場合、 **選択されたプロジェクトをソース管理に追加**ソース管理対象のソリューションに属しているプロジェクトに追加するコマンドで、プロジェクトをソース管理されたソリューションのサブフォルダーとして追加するかを追加するかどうかを求められます別のフォルダーとしてプロジェクトです。  
  
3.  ログオンを指示するメッセージが表示されたら、ソース管理プロバイダーにログオンします。  
  
4.  **Sourcesafe に追加** ダイアログ ボックスが表示されます。 プロジェクトの名前が表示されます、**プロジェクト**ボックス。  
  
5.  **フォルダー**ボックスの一覧で、プロジェクトを配置するフォルダーを開きます。 クリックする代わりに、**作成**に表示される名前のフォルダーを作成する、**プロジェクト**ボックス。  
  
## <a name="see-also"></a>参照  
 [ソース管理へのソリューションとプロジェクトの追加](../../2014/database-engine/add-solutions-and-projects-to-source-control.md)  
  
  
