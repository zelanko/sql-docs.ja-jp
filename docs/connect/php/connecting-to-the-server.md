---
title: "サーバーへの接続 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: php
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c251a239-e0bd-4f45-9207-b76651072dd0
caps.latest.revision: "44"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: c8f04b08517de9b21e5e3104b43b18db0324a863
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="connecting-to-the-server"></a>サーバーへの接続
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

このセクションのトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] で [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]に接続するためのオプションと手順について説明します。  

[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] は、Windows 認証または SQL Server 認証を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] に接続できます。 既定では、 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] は Windows 認証を使用してサーバーへの接続を試みます。  

## <a name="in-this-section"></a>このセクションの内容  

|トピック|説明|  
|---------|---------------|  
|[方法: Windows 認証を使用して接続する](../../connect/php/how-to-connect-using-windows-authentication.md)|Windows 認証を使用して接続を確立する方法について説明します。|  
|[方法: SQL Server 認証を使用して接続する](../../connect/php/how-to-connect-using-sql-server-authentication.md)|SQL Server 認証を使用して接続を確立する方法について説明します。|  
|[方法: Azure Active Directory 認証を使用して接続する](../../connect/php/azure-active-directory.md)|認証モードを設定し、Azure Active Directory id を使用して接続する方法について説明します。|  
|[方法: 指定されたポートで接続する](../../connect/php/how-to-connect-on-a-specified-port.md)|特定のポートでサーバーに接続する方法について説明します。|  
|[接続のプール](../../connect/php/connection-pooling-microsoft-drivers-for-php-for-sql-server.md)|ドライバーでの接続プールについて説明します。|  
|[方法: 複数のアクティブな結果セット (MARS) を無効にする](../../connect/php/how-to-disable-multiple-active-resultsets-mars.md)|接続するときに MARS 機能を無効にする方法について説明します。|  
|[接続オプション](../../connect/php/connection-options.md)|接続属性を格納する連想配列で許可されているオプションを示します。|  
|[PHP Driver for SQL Server Support for LocalDB (LocalDB 用 SQL Server サポート用 PHP ドライバー)](../../connect/php/php-driver-for-sql-server-support-for-localdb.md)|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] で追加された LocalDB 機能の [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)]によるサポートについて説明します。|  
|[高可用性、ディザスター リカバリーの PHP Driver for SQL Server のサポート](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)|機能が追加された高可用性、災害復旧を活用するために、アプリケーションを構成する方法について説明[!INCLUDE[ssSQL11](../../includes/sssql11_md.md)]です。|  
|[Microsoft Azure SQL Database への接続](../../connect/php/connecting-to-microsoft-azure-sql-database.md)|Azure SQL Database に接続する方法をについて説明します。|  
|[接続の復元性](../../connect/php/connection-resiliency.md)|接続が切断されたを再確立する接続の回復性機能について説明します。|  

## <a name="see-also"></a>参照  
[PHP SQL ドライバーのプログラミング ガイド](../../connect/php/programming-guide-for-php-sql-driver.md)
[サンプル アプリケーション &#40;です。SQLSRV ドライバー &#41;](../../connect/php/example-application-sqlsrv-driver.md)  
