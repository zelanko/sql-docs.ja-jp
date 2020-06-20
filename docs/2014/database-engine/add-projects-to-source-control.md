---
title: ソース管理にプロジェクトを追加する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- adding projects
- projects [SQL Server Management Studio], adding
ms.assetid: fd4616b2-a564-4a66-ac53-d1f5cba213c2
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: de32cbecdf132f1c881ab9fe5637af3a5c6cd400
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84937363"
---
# <a name="add-projects-to-source-control"></a>ソース管理へのプロジェクトの追加
  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ソリューションには、複数のスクリプト プロジェクトを含めることができます。 ソース管理にプロジェクトを追加する方法は、そのプロジェクトが属しているソリューションがソース管理の下にあるかどうかによって異なります。 ソリューションがソース管理の対象である場合は、ソリューションをチェックインすると、ソース管理にプロジェクトが自動的に追加されます。 ソリューションをチェックインする方法の詳細については、「[ファイルをチェックイン](../../2014/database-engine/check-in-files.md)する」を参照してください。  
  
 対象のプロジェクトが属しているソリューションがソース管理の対象でない場合は、ソリューションをソース管理に追加すると、ソリューションのプロジェクトが自動的に追加されます。 ソース管理にソリューションを追加する方法の詳細については、「[ソース管理へのソリューションの追加](../../2014/database-engine/add-solutions-to-source-control.md)」を参照してください。  
  
 ソース管理にソリューションを追加しない場合は、[**ソース管理に選択項目を追加**] コマンドを使用して、プロジェクトを手動で追加できます。  
  
 データベース オブジェクトはソース管理プロバイダーによって直接保護されませんが、データベース オブジェクトのスクリプトを作成し、そのスクリプトをソース管理の下で保存することができます。  
  
### <a name="to-add-a-project-to-source-control"></a>ソース管理にプロジェクトを追加するには  
  
1.  ソリューション エクスプローラーで、プロジェクトを選択します。  
  
2.  [**ファイル**] メニューの [**ソース管理**] をポイントし、[**選択したプロジェクトをソース管理に追加**] をクリックします。  
  
    > [!NOTE]  
    >  [**選択したプロジェクトをソース管理に追加**] コマンドを使用して、ソース管理されたソリューションに属するプロジェクトを追加する場合、ソース管理ソリューションのサブフォルダーとしてプロジェクトを追加するか、プロジェクトを別のフォルダーとして追加するかを確認するメッセージが表示されます。  
  
3.  ログオンを指示するメッセージが表示されたら、ソース管理プロバイダーにログオンします。  
  
4.  [ **Visual SourceSafe に追加**] ダイアログボックスが表示されます。 プロジェクトの名前が [**プロジェクト**] ボックスに表示されます。  
  
5.  [**フォルダー** ] ボックスの一覧で、プロジェクトを配置するフォルダーを開きます。 または、[**作成**] をクリックして、[**プロジェクト**] ボックスに表示された名前のフォルダーを作成することもできます。  
  
## <a name="see-also"></a>参照  
 [ソース管理へのソリューションとプロジェクトの追加](../../2014/database-engine/add-solutions-and-projects-to-source-control.md)  
  
  
