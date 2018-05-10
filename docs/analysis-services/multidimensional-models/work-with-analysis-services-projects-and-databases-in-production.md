---
title: 扱う Analysis Services プロジェクトおよび実稼働環境でデータベース |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 24d9bfecc768eac9f80120113fb532225a201990
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="work-with-analysis-services-projects-and-databases-in-production"></a>扱う Analysis Services プロジェクトおよび実稼働環境でのデータベース
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトから [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを開発して [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスに配置したら、配置したデータベース内のオブジェクトに対する変更方法を指定する必要があります。 セキュリティ ロール、パーティション分割、ストレージ設定などの変更は、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のいずれかを使用して行うことができます。 その他の変更 (属性やユーザー定義階層の追加など) を行うには、プロジェクト モードまたはオンライン モードで [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]を実行する必要があります。  
  
 オンライン モードの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で、配置した [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] データベースに変更を加えると、その直後に、配置で使用された [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトは期限切れになります。 開発担当者が [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクト内で変更を加え、変更したプロジェクトを配置しようとすると、データベース全体を上書きするように求めるメッセージが表示されます。 データベース全体を上書きする場合は、データベースの処理も必要になります。 配置されたデータベースを実稼働環境のスタッフが直接変更した場合は、その変更を開発チームに通知しておかないと、この問題は複雑になります。それは、開発チーム側が、自分たちが変更した内容が [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースに反映されていない理由を知らされないままとなるからです。  
  
 SQL Server の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ツールを使用すると、このような問題を未然に防ぐことができます。次の方法があります。  
  
-   方法 1 : [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースの実稼働環境バージョンに変更を加えるたびに、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] を使用して、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースの変更バージョンに基づいて新しい [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトを作成します。 この新しい [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトは、プロジェクトのマスター コピーとしてソース管理システムにチェックインできます。 この方法は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] をオンライン モードで使用して [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] データベースに変更を加えたかどうかに関係なく利用できます。  
  
-   方法 2 : [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] をプロジェクト モードで使用することにより、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] データベースの実稼働バージョンにのみ変更を加えます。 この方法では、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の配置ウィザードで利用できるオプションを使用して、セキュリティ ロールやストレージ設定など、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で加えられた変更を維持できます。 たとえば、プロジェクト ファイル内のデザイン関連設定を維持 (ストレージ設定およびセキュリティ ロールを除外) し、オンライン サーバーのストレージ設定およびセキュリティ ロールが使用されるようにすることができます。  
  
-   方法 3 : [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] をオンライン モードで使用することにより、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] データベースの実稼働バージョンにのみ変更を加えます。 SQL Server Management Studio と Business Intelligence Development Studio のいずれのツールも、同じオンライン サーバーだけを操作するので、バージョンが異なってもデータベースの同期が外れる可能性はありません。  
  
  
