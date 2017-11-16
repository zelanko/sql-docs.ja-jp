---
title: "XML ファイルへのポリシー ベースの管理ファセットの状態のコピー | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Policy-Based Management, copy facet state to XML file
ms.assetid: 7d604ab1-6dd6-4f8e-a79c-eba99ab106fd
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e709abcc199aa9365dc2ad4811d31c1f2019a495
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="copy-a-policy-based-management-facet-state-to-an-xml-file"></a>XML ファイルへのポリシー ベースの管理ファセットの状態のコピー
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でポリシー ベースの管理ファセットの状態を XML ファイルにコピーする方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [セキュリティ](#Security)  
  
-   **以下を使用してファセットの状態を XML ファイルにコピーするには:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> 権限  
 このトピックの手順では、msdb データベースの PolicyAdministratorRole ロールのメンバーシップが必要です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-copy-a-facet-state-to-an-xml-file"></a>ファセットの状態を XML ファイルにコピーするには  
  
1.  オブジェクト エクスプローラーで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンス、インスタンス オブジェクト、データベース、またはデータベース オブジェクトを右クリックし、 **[ファセット]**をクリックします。  
  
2.  **object_name**** ダイアログ ボックスで、 **現在の状態をポリシーとしてエクスポート**をクリックします。  
  
3.  **[ポリシーとしてエクスポート]** ダイアログ ボックスで、ファイルのパスと名前を入力します。または、参照ボタン (**[...]**) を使用してファイルを指定し、XML ファイルの名前を入力します。 このダイアログ ボックスで利用可能なオプションの詳細については、「 [Export As Policy Dialog Box](../../relational-databases/policy-based-management/export-as-policy-dialog-box.md)」を参照してください。  
  
4.  完了したら、 **[OK]**をクリックします。  
  
  
