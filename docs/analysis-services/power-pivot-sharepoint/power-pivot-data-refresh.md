---
title: Power Pivot データ更新 |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ppvt-sharepoint
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2647d94f0f1d8edc1d5c6ef9b364167f330e30a2
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2018
ms.locfileid: "38981444"
---
# <a name="power-pivot-data-refresh"></a>Power Pivot データ更新
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データを含むブックを作成したら、最初にブックを作成するときに使用したソースから更新情報を取得するクエリまたはコマンドを再実行して、定期的にデータを更新することができます。 このプロセスは **データ更新**と呼ばれます。データ更新は、 [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)]で要求時に実行したり、SharePoint ファーム内のアプリケーション サーバーで [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロセスとして実行される定期的な操作として実行したりすることができます。 詳細については、以下をご覧ください。  
  
-   [SharePoint 2010 での power Pivot データ更新](http://msdn.microsoft.com/01b54e6f-66e5-485c-acaa-3f9aa53119c9)  
  
-   [Power Pivot の構成自動データ更新アカウント (Power Pivot for SharePoint)](http://msdn.microsoft.com/81401eac-c619-4fad-ad3e-599e7a6f8493)  
  
-   [Power Pivot データ更新 (Power Pivot for SharePoint) の保存された資格情報を構成します。](http://msdn.microsoft.com/987eff0f-bcfe-4bbd-81e0-9aca993a2a75)  
  
-   [データ更新 (Power Pivot for SharePoint) のスケジュールします。](http://msdn.microsoft.com/8571208f-6aae-4058-83c6-9f916f5e2f9b)  
  
-   [データ更新履歴の表示 &#40;Power Pivot for SharePoint&#41;](../../analysis-services/power-pivot-sharepoint/view-data-refresh-history-power-pivot-for-sharepoint.md)  
  
> [!NOTE]  
>  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] および SharePoint Server 2013 の Excel Services がデータ更新のため、さまざまなアーキテクチャを使用して[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]データ モデル。 SharePoint 2013 でサポートされているアーキテクチャでは、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ モデルを読み込むための主要なコンポーネントとして Excel Services が使用されます。 以前に使用されていたデータ更新のアーキテクチャでは、データ モデルを読み込むために、SharePoint モードで [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービスおよび [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] を実行しているサーバーが使用されていました。 詳細については、以下を参照してください。  
>   
>  -   [SharePoint 2013 での PowerPivot データ更新](../../analysis-services/power-pivot-sharepoint/power-pivot-data-refresh-with-sharepoint-2013.md)  
> -   [ブックのアップグレードと定期データ更新 &#40;SharePoint 2013&#41;](../../analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md)  
  
  
