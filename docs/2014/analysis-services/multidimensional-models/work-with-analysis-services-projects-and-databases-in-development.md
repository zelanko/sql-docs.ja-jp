---
title: 開発段階での Analysis Services プロジェクトとデータベースの操作 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services, projects
ms.assetid: 39cf9166-fa92-40fe-9962-210a52461257
author: minewiskan
ms.author: owend
ms.openlocfilehash: 762ea6f33a94f65e7dd6895cd038d4a52d40d43e
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84535564"
---
# <a name="working-with-analysis-services-projects-and-databases-during-the-development-phase"></a>開発段階における Analysis Services プロジェクトおよびデータベースの操作
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] をプロジェクト モードまたはオンライン モードで使用すると、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] データベースを開発できます。  
  
## <a name="single-developer"></a>開発者が 1 人の場合  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベース全体とそれを構成するすべてのオブジェクトを 1 人の開発者が開発する場合、この開発者はビジネス インテリジェンス ソリューションのライフサイクル中はいつでも、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] をプロジェクト モードまたはオンライン モードで使用できます。 開発者が 1 人しかいない場合、どのモードを選択するかは特に重要ではありません。 オフライン プロジェクト ファイルの管理をソース管理システムと統合すると、アーカイブやロールバックなどのメリットが多数あります。 ただし、開発者が 1 人の場合は、変更内容を他の開発者に伝達する際の問題が生じません。  
  
## <a name="multiple-developers"></a>開発者が複数いる場合  
 同じビジネス インテリジェンス ソリューションに複数の開発者が取り組んでいる場合は、開発者がほとんどすべての状況においてプロジェクト モードでソース管理を行わないと、問題が生じます。 ソース管理を行うと、2 人の開発者によって同じオブジェクトに同時に変更が加えられるのを防ぐことができます。  
  
 たとえば、ある開発者がプロジェクト モードで作業し、特定のオブジェクトに変更を加えています。 この開発者が変更を加えている間に、配置済みのデータベースが別の開発者によってオンライン モードで変更されたとします。 この場合は、最初の開発者が変更後の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトを配置しようとすると問題が生じます。 つまり、配置済みデータベース内でオブジェクトが変更されたことが [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] によって検出され、データベース全体を上書きして、2 番目の開発者が加えた変更を上書きするように求めるメッセージが表示されます。 ただし、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] には、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベース インスタンスと上書き対象プロジェクト内のオブジェクトとの間で変更内容を解決する機能が用意されていません。したがって、最初の開発者に残された選択肢は、自分が加えた変更をすべて破棄し、最新バージョンの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースに基づいて新規のプロジェクトを作成し直すことだけです。  
  
  
