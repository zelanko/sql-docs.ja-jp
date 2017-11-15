---
title: "ログインの監査の構成 (SQL Server Management Studio) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- auditing [SQL Server]
- audits [SQL Server], logins
- logins [SQL Server], auditing
ms.assetid: 16961116-57ac-4eef-8037-791b26ade548
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 0e4c0913ac4b2a88370865e7de029c8e7e965497
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="configure-login-auditing-sql-server-management-studio"></a>ログインの監査の構成 (SQL Server Management Studio)
このトピックでは、 [!INCLUDE[ssCurrent](../includes/sscurrent_md.md)] のログイン操作を監視するために [!INCLUDE[ssDEnoversion](../includes/ssdenoversion_md.md)] でログインの監査を構成する方法について説明します。 次のイベントが発生したときにエラー ログに書き込むように、ログインの監査を構成できます。  
  
-   ログインの失敗  
  
-   ログインの成功  
  
-   [失敗したログインと成功したログインの両方]  
  
このオプションを有効にするには、 [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] を再起動する必要があります。  
  
## <a name="SSMSProcedure"></a>SQL Server Management Studio の使用  
  
#### <a name="to-configure-login-auditing"></a>ログインの監査を構成するには  
  
1.  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)]で、オブジェクト エクスプローラーを使用して [!INCLUDE[ssDEnoversion](../includes/ssdenoversion_md.md)] のインスタンスに接続します。  
  
2.  オブジェクト エクスプローラーでサーバー名を右クリックし、 **[プロパティ]**をクリックします。  
  
3.  **[セキュリティ]** ページの **[ログインの監査]** で、必要なオプションをクリックし、 **[サーバーのプロパティ]** ページを閉じます。  
  
4.  オブジェクト エクスプローラーでサーバー名を右クリックし、 **[再起動]**をクリックします。  
  
