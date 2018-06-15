---
title: 扱う Analysis Services プロジェクトおよびデータベース開発で |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 018f937ed07c202aad17d5e7758f41a3082c4870
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34027542"
---
# <a name="work-with-analysis-services-projects-and-databases-in-development"></a>扱う Analysis Services プロジェクトおよびデータベース開発
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] をプロジェクト モードまたはオンライン モードで使用すると、[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] データベースを開発できます。  
  
## <a name="single-developer"></a>開発者が 1 人の場合  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベース全体とそれを構成するすべてのオブジェクトを 1 人の開発者が開発する場合、この開発者はビジネス インテリジェンス ソリューションのライフサイクル中はいつでも、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] をプロジェクト モードまたはオンライン モードで使用できます。 開発者が 1 人しかいない場合、どのモードを選択するかは特に重要ではありません。 オフライン プロジェクト ファイルの管理をソース管理システムと統合すると、アーカイブやロールバックなどのメリットが多数あります。 ただし、開発者が 1 人の場合は、変更内容を他の開発者に伝達する際の問題が生じません。  
  
## <a name="multiple-developers"></a>開発者が複数いる場合  
 同じビジネス インテリジェンス ソリューションに複数の開発者が取り組んでいる場合は、開発者がほとんどすべての状況においてプロジェクト モードでソース管理を行わないと、問題が生じます。 ソース管理を行うと、2 人の開発者によって同じオブジェクトに同時に変更が加えられるのを防ぐことができます。  
  
 たとえば、ある開発者がプロジェクト モードで作業し、特定のオブジェクトに変更を加えています。 この開発者が変更を加えている間に、配置済みのデータベースが別の開発者によってオンライン モードで変更されたとします。 この場合は、最初の開発者が変更後の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトを配置しようとすると問題が生じます。 つまり、配置済みデータベース内でオブジェクトが変更されたことが [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] によって検出され、データベース全体を上書きして、2 番目の開発者が加えた変更を上書きするように求めるメッセージが表示されます。 ただし、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] には、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベース インスタンスと上書き対象プロジェクト内のオブジェクトとの間で変更内容を解決する機能が用意されていません。したがって、最初の開発者に残された選択肢は、自分が加えた変更をすべて破棄し、最新バージョンの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースに基づいて新規のプロジェクトを作成し直すことだけです。  
  
  
