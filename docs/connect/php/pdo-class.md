---
title: PDO クラス |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 9c77b68d-0649-44af-96fa-586cbb319f5f
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 948c11c97bc9d155f3890f4d11aac54cd0ae4735
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35308171"
---
# <a name="pdo-class"></a>PDO クラス
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

PDO クラスには、PHP アプリケーションが [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] インスタンスに接続できるようにするメソッドが含まれています。  
  
## <a name="syntax"></a>構文  
  
```  
  
PDO {}  
```  
  
## <a name="remarks"></a>コメント  
PDO クラスには次のメソッドが含まれています。  
  
[PDO::__construct](../../connect/php/pdo-construct.md)  

[PDO::beginTransaction](../../connect/php/pdo-begintransaction.md)  
  
[PDO::commit](../../connect/php/pdo-commit.md)  
  
[PDO::errorCode](../../connect/php/pdo-errorcode.md)  
  
[PDO::errorInfo](../../connect/php/pdo-errorinfo.md)  
  
[PDO::exec](../../connect/php/pdo-exec.md)  
  
[PDO::getAttribute](../../connect/php/pdo-getattribute.md)  
  
[PDO::getAvailableDrivers](../../connect/php/pdo-getavailabledrivers.md)  
  
[PDO::lastInsertId](../../connect/php/pdo-lastinsertid.md)  
  
[PDO::prepare](../../connect/php/pdo-prepare.md)  
  
[PDO::query](../../connect/php/pdo-query.md)  
  
[PDO::quote](../../connect/php/pdo-quote.md)  
  
[PDO::rollback](../../connect/php/pdo-rollback.md)  
  
[PDO::setAttribute](../../connect/php/pdo-setattribute.md)  
  
PDO のサポートは [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]のバージョン 2.0 で追加されました。  
  
## <a name="see-also"></a>参照  
[PDO_SQLSRV ドライバー リファレンス](../../connect/php/pdo-sqlsrv-driver-reference.md)

[Microsoft Drivers for PHP for SQL Server の概要](../../connect/php/overview-of-the-php-sql-driver.md)

[定数 &#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)

[For PHP for SQL Server の Microsoft drivers ガイドのプログラミング](../../connect/php/programming-guide-for-php-sql-driver.md)

[入門 Microsoft Drivers for PHP for SQL Server](../../connect/php/getting-started-with-the-php-sql-driver.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
