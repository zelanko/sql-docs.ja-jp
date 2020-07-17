---
title: SQL Server インスタンスへのログイン (コマンド プロンプト) | Microsoft Docs
description: "\"sqlcmd\" ユーティリティについて説明します。 コマンド プロンプトでこれを使用して、SQL Server のインスタンスへの接続をテストする方法について説明します。"
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- logins [SQL Server], named instance of SQL Server
- log ins [SQL Server]
- logins [SQL Server], default instance of SQL Server
- command prompt [SQL Server], logins
- logging in [SQL Server]
ms.assetid: f67c11e3-c519-40c9-82c1-07efa9d9985e
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 0723a5d463757eca93dd7bacb1fc2b8fe232cdd8
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85772406"
---
# <a name="log-in-to-an-instance-of-sql-server-command-prompt"></a>SQL Server インスタンスへのログイン (コマンド プロンプト)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]sqlcmd **ユーティリティを使用して** のインスタンスへの接続をテストする方法について説明します。  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-log-in-to-the-default-instance-of-sql-server"></a>SQL Server の既定のインスタンスにログインするには  
  
1.  コマンド プロンプトで次のコマンドを入力し、Windows 認証を使用して接続します。  
  
    ```  
    sqlcmd [ /E ] [ /S servername ]  
  
    ```  
  
#### <a name="to-log-in-to-a-named-instance-of-sql-server"></a>SQL Server の名前付きインスタンスにログインするには  
  
1.  コマンド プロンプトで次のコマンドを入力し、Windows 認証を使用して接続します。  
  
    ```  
    sqlcmd [ /E ] /S servername\instancename  
  
    ```  
  
## <a name="see-also"></a>参照  
 [sqlcmd ユーティリティ](../../tools/sqlcmd-utility.md)   
 [osql ユーティリティ](../../tools/osql-utility.md)  
  
  
