---
title: 使用 Analysis Services プロジェクトおよび実稼働環境でのデータベース |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f90af41c397da20fb26c73bebc6723b9a3cf6270
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62743238"
---
# <a name="work-with-analysis-services-projects-and-databases-in-production"></a>使用 Analysis Services プロジェクトおよび実稼働環境でのデータベース
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトから [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを開発して [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスに配置したら、配置したデータベース内のオブジェクトに対する変更方法を指定する必要があります。 セキュリティ ロール、パーティション分割、ストレージ設定などの変更は、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のいずれかを使用して行うことができます。 その他の変更 (属性やユーザー定義階層の追加など) を行うには、プロジェクト モードまたはオンライン モードで [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]を実行する必要があります。  
  
 オンライン モードの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で、配置した [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] データベースに変更を加えると、その直後に、配置で使用された [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトは期限切れになります。 開発担当者が [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクト内で変更を加え、変更したプロジェクトを配置しようとすると、データベース全体を上書きするように求めるメッセージが表示されます。 データベース全体を上書きする場合は、データベースの処理も必要になります。 配置されたデータベースを実稼働環境のスタッフが直接変更した場合は、その変更を開発チームに通知しておかないと、この問題は複雑になります。それは、開発チーム側が、自分たちが変更した内容が [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースに反映されていない理由を知らされないままとなるからです。  
  
 SQL Server の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ツールを使用すると、このような問題を未然に防ぐことができます。次の方法があります。  
  
-   方法 1:Production バージョンに変更が行われるたびに、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]データベースを使用して[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]新たに作成する[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]プロジェクトの変更したバージョンに基づいて、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]データベース。 この新しい [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトは、プロジェクトのマスター コピーとしてソース管理システムにチェックインできます。 この方法は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] をオンライン モードで使用して [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] データベースに変更を加えたかどうかに関係なく利用できます。  
  
-   方法 2:唯一の production バージョンに変更を[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]を使用してデータベース[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]または[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]プロジェクト モードでします。 この方法では、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の配置ウィザードで利用できるオプションを使用して、セキュリティ ロールやストレージ設定など、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で加えられた変更を維持できます。 たとえば、プロジェクト ファイル内のデザイン関連設定を維持 (ストレージ設定およびセキュリティ ロールを除外) し、オンライン サーバーのストレージ設定およびセキュリティ ロールが使用されるようにすることができます。  
  
-   方法 3:唯一の production バージョンに変更を[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]を使用してデータベース[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]または[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]オンライン モードでします。 SQL Server Management Studio と Business Intelligence Development Studio のいずれのツールも、同じオンライン サーバーだけを操作するので、バージョンが異なってもデータベースの同期が外れる可能性はありません。  
  
  
