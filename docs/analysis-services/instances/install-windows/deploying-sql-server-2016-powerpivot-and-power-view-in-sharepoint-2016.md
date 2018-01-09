---
title: "SQL Server 2016 PowerPivot と SharePoint 2016 の Power View の配置 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d0a9834-db91-403f-847c-79a8f49fc916
caps.latest.revision: "7"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 166ce8f52401d5cd5cad70e19aea37871d57afe4
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="deploying-sql-server-2016-powerpivot-and-power-view-in-sharepoint-2016"></a>SharePoint 2016 での SQL Server 2016 PowerPivot と Power View の配置
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]**概要:**このホワイト ペーパーは SharePoint 管理者やアーキテクト詳細な手順を展開して、SharePoint サーバーのプレビュー リリースに基づいて、Microsoft BI デモ環境を構成します。2016、office Online Server、および SQL Server 2016 BI スタックの SharePoint 2016 用です。 重要なアーキテクチャの変更とそれに対応するシステムの依存関係について簡単に説明した後、ソフトウェアと構成の要件のほか、3 つの段階で BI の機能を有効にして確認できる推奨配置パスについて概説されています。 また、このホワイト ペーパーでは、SharePoint Server 2016 Beta 2、Office Online Server Preview、SQL Server 2016 CTP 3.1 リリースにおける既知の問題が取り扱われており、適切な回避策が提示されています。 これらの回避策は、各製品の最終バージョンでは不要になります。 RTM リリースを配置する際には、このホワイト ペーパーの更新されたバージョンをご確認ください。  
  
 **ライター:** Kay Unkroth  
  
 **テクニカル レビュー担当者:** Adam Saxton、Anne Zorner、Craig Guyer、Frank Weigel、Gregory Appel、Heidi Steen、 Jason Haak、Kasper de Jonge、Kirk Stark、Klaus Sobel、Mike Plumley、Mike Taghizadeh、Patrick Wheeler、Riccardo Muti、Steve Hord  
  
 **公開日:** 2015 年 12 月  
  
 **適用対象:** SQL Server 2016 CTP3.1、SharePoint 2016 Preview、Office Online Server Preview  
  
 このドキュメントをご覧になる場合は、Word 文書「 [SharePoint 2016 での SQL Server 2016 PowerPivot と Power View の配置](http://download.microsoft.com/download/D/2/0/D20E1C5F-72EA-4505-9F26-FEF9550EFD44/Deploying%20SQL%20Server%202016%20PowerPivot%20and%20Power%20View%20in%20SharePoint%202016.docx) 」をダウンロードしてください。  
  
  
