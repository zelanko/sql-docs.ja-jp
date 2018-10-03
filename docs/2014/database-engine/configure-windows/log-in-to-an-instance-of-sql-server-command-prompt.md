---
title: SQL Server インスタンスへのログイン (コマンド プロンプト) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- logins [SQL Server], named instance of SQL Server
- log ins [SQL Server]
- logins [SQL Server], default instance of SQL Server
- command prompt [SQL Server], logins
- logging in [SQL Server]
ms.assetid: f67c11e3-c519-40c9-82c1-07efa9d9985e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d6ba115fef26547528175e012322c1043f019211
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48067982"
---
# <a name="log-in-to-an-instance-of-sql-server-command-prompt"></a>SQL Server インスタンスへのログイン (コマンド プロンプト)
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
  
  
