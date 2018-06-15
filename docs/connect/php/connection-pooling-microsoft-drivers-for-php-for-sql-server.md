---
title: 接続のプール (Microsoft Drivers for PHP for SQL Server) |Microsoft ドキュメント
ms.custom: ''
ms.date: 07/10/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- connection pooling support
ms.assetid: 4d9a83d4-08de-43a1-975c-0a94005edc94
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: eb23d95aeebfbc44db876d64a96add890d17e806
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35307181"
---
# <a name="connection-pooling-microsoft-drivers-for-php-for-sql-server"></a>接続のプール (Microsoft SQL Server 用 Drivers for PHP)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]の接続のプールについて重要な点は、次のとおりです。  
  
-   [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] では ODBC 接続プールが使用されます。  
  
-   既定では、接続プールは Windows で有効にします。 Linux および Mac OS X の場合は、ODBC の接続プールが有効になっている場合にのみ、接続はプールされます。 接続プールが有効になっているし、サーバーに接続する、ドライバーは、新しいものを作成する前に、プールされた接続を使用しようとします。 プールに同等の接続がない場合、新しい接続が構築され、プールに追加されます。 ドライバーは、接続文字列の比較に基づき、接続が同等かどうかを判断します。  
  
-   プールの接続が使用されると、接続状態がリセットされます。  
  
-   接続を閉じると、接続がプールに返されます。  
  
接続プールの詳細については、次を参照してください。[ドライバー マネージャーの接続のプール](../../odbc/reference/develop-app/driver-manager-connection-pooling.md)です。  
  
## <a name="enablingdisabling-connection-pooling"></a>有効化/無効にする接続プール
### <a name="windows"></a>Windows
値を設定して (接続プールで同等の接続を探して) ではなく、新しい接続を作成するドライバーを強制することができます、 *ConnectionPooling*への接続文字列内の属性**false** (または 0) です。  
  
場合、 *ConnectionPooling*属性が、接続文字列から省略するかに設定されているかどうかは**true** (または 1)、ドライバーを作成するだけの新しい接続では、同等の接続が存在しない場合、接続プールです。  
  
その他の接続属性の詳細については、「 [Connection Options](../../connect/php/connection-options.md)」を参照してください。  
### <a name="linux-and-mac-os-x"></a>Linux および Mac OS X
*ConnectionPooling*属性は、接続プールを有効/無効にするには使用できません。 

接続プールできます有効/無効にする odbcinst.ini 構成ファイルを編集することによってです。 ドライバーは、変更を有効にするために再読み込みする必要があります。

設定`Pooling`に`Yes`、正の値と`CPTimeout`odbcinst.ini 内の値は、接続プールを有効になります。 
```
[ODBC]
Pooling=Yes

[ODBC Driver 13 for SQL Server]
CPTimeout=<int value>
```
設定`Pooling`に`No`odbcinst.ini のドライバーは強制的に新しい接続を作成します。
```
[ODBC]
Pooling=No
```
  
## <a name="see-also"></a>参照  
[方法: Windows 認証を使用して接続する](../../connect/php/how-to-connect-using-windows-authentication.md)

[方法: SQL Server 認証を使用して接続する](../../connect/php/how-to-connect-using-sql-server-authentication.md)  
  
