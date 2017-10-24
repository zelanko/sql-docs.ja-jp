---
title: "PowerPivot を展開し、Power View の多層 SharePoint 2016 ファーム |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e36a632-0750-4247-92b6-1fe38c7a4ce2
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d7dc4fc8e7b1926359096447183dc17c9c1a1cd8
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="deploy-powerpivot-and-power-view---multi-tier-sharepoint-2016-farm"></a>PowerPivot を展開し、Power View の多層 SharePoint 2016 ファーム
  **概要:** このホワイト ペーパーでは、SharePoint の管理者と設計者向けに、複数のサーバーが含まれる SharePoint ファーム内で Microsoft BI デモ環境を配置、構成する詳細な手順を説明しています。このホワイト ペーパーは SharePoint Server 2016、Office Online Server、および SharePoint 2016 用 SQL Server 2016 BI スタックのプレビュー リリースに基づいています。 重要なアーキテクチャの変更とそれに対応するシステムの依存関係について簡単に説明した後、ソフトウェアと構成の要件のほか、3 つの段階で BI の機能を有効にして確認できる推奨配置パスについて概説されています。 また、このホワイト ペーパーでは、SharePoint Server 2016 Beta 2、Office Online Server Preview、SQL Server 2016 CTP 3.1 リリースにおける既知の問題が取り扱われており、適切な回避策が提示されています。 これらの回避策は、各製品の最終バージョンでは不要になります。 RTM リリースを配置する際には、このホワイト ペーパーの更新されたバージョンをご確認ください。  
  
 **ライター:**Kay Unkroth、Jason Haak  
  
 **テクニカル レビュー担当者:** Adam Saxton、Anne Zorner、Craig Guyer、Frank Weigel、Gregory Appel、Heidi Steen、Kasper de Jonge、Kirk Stark、Klaus Sobel、Mike Plumley、Mike Taghizadeh、Patrick Wheeler、Riccardo Muti、Steve Hord  
  
 **公開日:**2016 年 1 月  
  
 **適用対象:** SQL Server 2016 CTP3.1、SharePoint 2016 Preview、Office Online Server Preview  
  
 このドキュメントをご覧になる場合は、Word 文書「 [多層 SharePoint 2016 ファームでの SQL Server 2016 PowerPivot と Power View の配置](http://download.microsoft.com/download/D/2/0/D20E1C5F-72EA-4505-9F26-FEF9550EFD44/Deploying%20SQL%20Server%202016%20PowerPivot%20and%20Power%20View%20in%20a%20Multi-Tier%20SharePoint%202016%20Farm.docx) 」をダウンロードしてください。  
  
  

