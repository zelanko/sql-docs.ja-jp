---
title: XML ファイルへのポリシー ベースの管理ファセットの状態のコピー | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, copy facet state to XML file
ms.assetid: 7d604ab1-6dd6-4f8e-a79c-eba99ab106fd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1daea321a8d81b3476b6abb7eb328f5d59c9df41
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85068963"
---
# <a name="copy-a-policy-based-management-facet-state-to-an-xml-file"></a>XML ファイルへのポリシー ベースの管理ファセットの状態のコピー
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でポリシー ベースの管理ファセットの状態を XML ファイルにコピーする方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [Security](#Security)  
  
-   **以下を使用してファセットの状態を XML ファイルにコピーするには:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="security"></a><a name="Security"></a> セキュリティ  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 このトピックの手順では、msdb データベースの PolicyAdministratorRole ロールのメンバーシップが必要です。  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-copy-a-facet-state-to-an-xml-file"></a>ファセットの状態を XML ファイルにコピーするには  
  
1.  オブジェクト エクスプローラーで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンス、インスタンス オブジェクト、データベース、またはデータベース オブジェクトを右クリックし、 **[ファセット]** をクリックします。  
  
2.  **[ファセットを表示 -**_オブジェクト名_] ダイアログ ボックスで、**[現在の状態をポリシーとしてエクスポート]** をクリックします。  
  
3.  **[ポリシーとしてエクスポート]** ダイアログ ボックスで、ファイルのパスと名前を入力します。または、参照ボタン (**[...]**) を使用してファイルを指定し、XML ファイルの名前を入力します。 このダイアログ ボックスで利用可能なオプションの詳細については、「 [Export As Policy Dialog Box](export-as-policy-dialog-box.md)」を参照してください。  
  
4.  完了したら、[**OK**] をクリックします。  
  
  
