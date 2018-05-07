---
title: sqlsrv_configure |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- sqlsrv_configure
apitype: NA
helpviewer_keywords:
- sqlsrv_configure
- API Reference, sqlsrv_configure
ms.assetid: 9393f975-a4ef-4c50-b4dd-14892fc55cc9
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 449c20bcbe3ff21675c51f483519607d5c37b034
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqlsrvconfigure"></a>sqlsrv_configure
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

エラー処理とログ記録のオプションの設定を変更します。  
  
## <a name="syntax"></a>構文  
  
```  
  
sqlsrv_configure( string $setting, mixed $value )  
```  
  
#### <a name="parameters"></a>パラメーター  
*$setting*: 構成する設定の名前です。 設定の一覧については、次の表を参照してください。  
  
*$value*: *$setting* パラメーターで指定された設定に適用する値です。 このパラメーターに指定できる値は、指定されている設定によって異なります。 次の表に、考えられる組み合わせを示します。  
  
|設定|$value パラメーターに使用可能な値 (かっこ内と同等の整数)|既定値|  
|-----------|------------------------------------------------------------------------------|-----------------|  
|ClientBufferMaxKBSize<sup>1</sup>|PHP メモリの上限に達するまでの負以外の数値。<br /><br />ゼロ (0) は、バッファーのサイズに制限がないことを意味します。|10240|  
|LogSeverity<sup>2</sup>|SQLSRV_LOG_SEVERITY_ALL (-1)<br /><br />SQLSRV_LOG_SEVERITY_ERROR (1)<br /><br />SQLSRV_LOG_SEVERITY_NOTICE (4)<br /><br />SQLSRV_LOG_SEVERITY_WARNING (2)|SQLSRV_LOG_SEVERITY_ERROR (1)|  
|LogSubsystems<sup>2</sup>|SQLSRV_LOG_SYSTEM_ALL (-1)<br /><br />SQLSRV_LOG_SYSTEM_CONN (2)<br /><br />SQLSRV_LOG_SYSTEM_INIT (1)<br /><br />SQLSRV_LOG_SYSTEM_OFF (0)<br /><br />SQLSRV_LOG_SYSTEM_STMT (4)<br /><br />SQLSRV_LOG_SYSTEM_UTIL (8)|SQLSRV_LOG_SYSTEM_OFF (0)|  
|WarningsReturnAsErrors<sup>3</sup>|**true** (1) または**false** (0)|**true** (1)|  
  
## <a name="return-value"></a>戻り値  
サポートされていない設定または値を使用して **sqlsrv_configure** 関数を呼び出すと、この関数は **false**を返します。 それ以外の場合は、 **true**を返します。  
  
## <a name="remarks"></a>解説  
(1) のクライアント側クエリの詳細については、次を参照してください。[カーソルの種類&#40;SQLSRV ドライバー&#41;](../../connect/php/cursor-types-sqlsrv-driver.md)です。  
  
(2) のログ記録アクティビティの詳細については、次を参照してください。 [Logging Activity](../../connect/php/logging-activity.md)です。  
  
(3) のエラーおよび警告の処理の構成に関する詳細については、次を参照してください。[する方法: エラーおよび警告の処理、SQLSRV ドライバーを使用して構成する](../../connect/php/how-to-configure-error-and-warning-handling-using-the-sqlsrv-driver.md)です。  
  
## <a name="see-also"></a>参照  
[SQLSRV ドライバー API リファレンス](../../connect/php/sqlsrv-driver-api-reference.md)

[For PHP for SQL Server の Microsoft drivers ガイドのプログラミング](../../connect/php/programming-guide-for-php-sql-driver.md) 
  
