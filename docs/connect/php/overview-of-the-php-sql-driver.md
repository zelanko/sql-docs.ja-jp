---
title: Microsoft Drivers for PHP for SQL Server の概要 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 66559249-34c0-409d-b919-9b5bf0c4c9ec
caps.latest.revision: 73
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c44d3278a61f8df573c909a48507624c563df64b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="overview-of-the-microsoft-drivers-for-php-for-sql-server"></a>Microsoft Drivers for PHP for SQL Server の概要

[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]は、SQL Server 2005 およびそれ以降のバージョンの Azure SQL データベースを含むデータ アクセスを提供する PHP 拡張機能です。 拡張機能は、SQL Server Express、SQL Server 2005 以降のすべてのバージョンのデータにアクセスするため、SQLSRV ドライバーの手続き型のインターフェイスと、PDO_SQLSRV ドライバーでのオブジェクト指向のインターフェイスを提供します。 バージョン 3.1 および以降のドライバーのサポートは、SQL Server 2008 で開始します。 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] API には、Windows 認証、トランザクション、パラメーター バインディング、ストリーミング、メタデータ アクセス、およびエラー処理のサポートが含まれています。  
  
使用する、[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]正しいバージョンの SQL Server Native Client が必要、または PHP の同じコンピューターにインストールされている Microsoft ODBC ドライバーが実行されています。  詳細については、次を参照してください。 [Microsoft Drivers for PHP for SQL Server のシステム要件](../../connect/php/system-requirements-for-the-php-sql-driver.md)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|Description|  
|---------|---------------|  
| ![ダウンロード DownArrow 丸](../../ssdt/media/download.png)[for PHP for SQL Server ドライバーをダウンロードするには](download-drivers-php-sql-server.md) | For PHP for SQL Server の Microsoft ドライバーのダウンロードにリンクします。 |
|[Microsoft Drivers for PHP for SQL Server のリリース ノート](../../connect/php/release-notes-for-the-php-sql-driver.md)|バージョン 4.0、3.2、3.1、3.0、および 2.0 で追加された機能を一覧表示します。|  
|[サポート リソースを Microsoft Drivers for PHP for SQL Server](../../connect/php/support-resources-for-the-php-sql-driver.md)|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]を使用するアプリケーションを開発するときに役立つリソースへのリンクを示します。|  
|[ドキュメントのコード例について](../../connect/php/about-code-examples-in-the-documentation.md)|このドキュメントのコード例を実行するときに役立つ情報を提供します。|  
  
## <a name="reference"></a>リファレンス  
[SQLSRV ドライバー API リファレンス](../../connect/php/sqlsrv-driver-api-reference.md)  
[PDO_SQLSRV ドライバー リファレンス](../../connect/php/pdo-sqlsrv-driver-reference.md)  
[定数 &#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)  
  
## <a name="see-also"></a>参照  
[入門 Microsoft Drivers for PHP for SQL Server](../../connect/php/getting-started-with-the-php-sql-driver.md)

[For PHP for SQL Server の Microsoft drivers ガイドのプログラミング](../../connect/php/programming-guide-for-php-sql-driver.md)

[サンプル アプリケーション &#40;SQLSRV ドライバー&#41;](../../connect/php/example-application-sqlsrv-driver.md)
