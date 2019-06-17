---
title: PowerPivot の配置し、Power View - 多層 SharePoint 2016 ファーム |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ppvt-sharepoint
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ee295f354de5479f5af8add49cb7aee2985a687f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63054613"
---
# <a name="deploy-powerpivot-and-power-view---multi-tier-sharepoint-2016-farm"></a>PowerPivot の配置し、Power View - 多層 SharePoint 2016 ファーム
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  **概要:** まとめ:このホワイト ペーパーは SharePoint の管理者と配置、SharePoint サーバーのプレビュー リリースに基づいて、複数のサーバーと SharePoint ファームで、Microsoft BI デモ環境を構成する詳細な手順についてをアーキテクト2016、office Online Server、および SQL Server 2016 の BI は、SharePoint 2016 用スタックします。 重要なアーキテクチャの変更とそれに対応するシステムの依存関係について簡単に説明した後、ソフトウェアと構成の要件のほか、3 つの段階で BI の機能を有効にして確認できる推奨配置パスについて概説されています。 また、このホワイト ペーパーでは、SharePoint Server 2016 Beta 2、Office Online Server Preview、SQL Server 2016 CTP 3.1 リリースにおける既知の問題が取り扱われており、適切な回避策が提示されています。 これらの回避策は、各製品の最終バージョンでは不要になります。 RTM リリースを配置する際には、このホワイト ペーパーの更新されたバージョンをご確認ください。  
  
 **ライター:** Kay Unkroth、Jason Haak  
  
 **技術校閲者:** Adam Saxton、Anne Zorner、Craig Guyer、Frank Weigel、Gregory Appel、Heidi Steen、Kasper de Jonge、Kirk Stark、Klaus Sobel、Mike Plumley、Mike Taghizadeh、Patrick Wheeler、Riccardo Muti、Steve Hord  
  
 **公開日:** 2016 年 1 月  
  
 **適用対象:** SQL Server 2016 CTP3.1、SharePoint 2016 Preview、Office Online Server Preview  
  
 このドキュメントをご覧になる場合は、Word 文書「 [多層 SharePoint 2016 ファームでの SQL Server 2016 PowerPivot と Power View の配置](http://download.microsoft.com/download/D/2/0/D20E1C5F-72EA-4505-9F26-FEF9550EFD44/Deploying%20SQL%20Server%202016%20PowerPivot%20and%20Power%20View%20in%20a%20Multi-Tier%20SharePoint%202016%20Farm.docx) 」をダウンロードしてください。  
  
  
