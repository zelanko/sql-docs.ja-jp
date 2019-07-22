---
title: XML ファイルへのポリシー ベースの管理ファセットの状態のコピー | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, copy facet state to XML file
ms.assetid: 7d604ab1-6dd6-4f8e-a79c-eba99ab106fd
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: c0e3d197f8cb6b7b5bd05ed037fd32e938b5ad4f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68109733"
---
# <a name="copy-a-policy-based-management-facet-state-to-an-xml-file"></a>XML ファイルへのポリシー ベースの管理ファセットの状態のコピー
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でポリシー ベースの管理ファセットの状態を XML ファイルにコピーする方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [セキュリティ](#Security)  
  
-   **以下を使用してファセットの状態を XML ファイルにコピーするには:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 このトピックの手順では、msdb データベースの PolicyAdministratorRole ロールのメンバーシップが必要です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-copy-a-facet-state-to-an-xml-file"></a>ファセットの状態を XML ファイルにコピーするには  
  
1.  オブジェクト エクスプローラーで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンス、インスタンス オブジェクト、データベース、またはデータベース オブジェクトを右クリックし、 **[ファセット]** をクリックします。  
  
2.  **[ファセットを表示 -** _オブジェクト名_] ダイアログ ボックスで、 **[現在の状態をポリシーとしてエクスポート]** をクリックします。  
  
3.  **[ポリシーとしてエクスポート]** ダイアログ ボックスで、ファイルのパスと名前を入力します。または、参照ボタン ( **[...]** ) を使用してファイルを指定し、XML ファイルの名前を入力します。 このダイアログ ボックスで利用可能なオプションの詳細については、「 [Export As Policy Dialog Box](../../relational-databases/policy-based-management/export-as-policy-dialog-box.md)」を参照してください。  
  
4.  完了したら、 **[OK]** をクリックします。  
  
  
