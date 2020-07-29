---
title: ログインの監査の構成 (SQL Server Management Studio)
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- auditing [SQL Server]
- audits [SQL Server], logins
- logins [SQL Server], auditing
ms.assetid: 16961116-57ac-4eef-8037-791b26ade548
author: markingmyname
ms.author: maghan
ms.openlocfilehash: a203bc3f3c63c89cb94fad935e74197d81b77331
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "86921203"
---
# <a name="configure-login-auditing-sql-server-management-studio"></a>ログインの監査の構成 (SQL Server Management Studio)
[!INCLUDE[sqlserver](../includes/applies-to-version/sqlserver.md)]
このトピックでは、[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]のログイン操作を監視するために [!INCLUDE[ssDEnoversion](../includes/ssdenoversion_md.md)] でログインの監査を構成する方法について説明します。 次のイベントが発生したときにエラー ログに書き込むように、ログインの監査を構成できます。  
  
-   ログインの失敗  
  
-   ログインの成功  
  
-   [失敗したログインと成功したログインの両方]  
  
このオプションを有効にするには、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] を再起動する必要があります。  
  
## <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a>SQL Server Management Studio の使用  
  
#### <a name="to-configure-login-auditing"></a>ログインの監査を構成するには  
  
1.  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]で、オブジェクト エクスプローラーを使用して [!INCLUDE[ssDEnoversion](../includes/ssdenoversion_md.md)] のインスタンスに接続します。  
  
2.  オブジェクト エクスプローラーでサーバー名を右クリックし、 **[プロパティ]** をクリックします。  
  
3.  **[セキュリティ]** ページの **[ログインの監査]** で、必要なオプションをクリックし、 **[サーバーのプロパティ]** ページを閉じます。  
  
4.  オブジェクト エクスプローラーでサーバー名を右クリックし、 **[再起動]** をクリックします。  
  
