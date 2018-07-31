---
title: PDOStatement::getAttribute |Microsoft Docs
ms.custom: ''
ms.date: 07/13/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 41d0cca3-8556-4573-bb90-8e9402d9379f
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e2c02170c88066ed30b99fb1fca46505b099752f
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37983283"
---
# <a name="pdostatementgetattribute"></a>PDOStatement::getAttribute
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

定義済みの PDOStatement 属性またはカスタム ドライバー属性の値を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
mixed PDOStatement::getAttribute( $attribute );  
```  
  
#### <a name="parameters"></a>パラメーター  
$*attribute*: PDO::ATTR_* または PDO::SQLSRV_ATTR_\* 定数のいずれかの整数。 サポートされている属性で設定できる属性[pdostatement::setattribute](../../connect/php/pdostatement-setattribute.md)、pdo::sqlsrv_attr_direct_query (詳細については、次を参照してください[直接ステートメント実行と準備されたステートメントの実行で。PDO_SQLSRV ドライバー](../../connect/php/direct-statement-execution-prepared-statement-execution-pdo-sqlsrv-driver.md))、pdo::attr_cursor および pdo::sqlsrv_attr_cursor_scroll_type (詳細については、次を参照してください。[カーソルの種類 (PDO_SQLSRV ドライバー)](../../connect/php/cursor-types-pdo-sqlsrv-driver.md))。  
  
## <a name="return-value"></a>戻り値  
成功した場合、定義済みの PDO 属性またはカスタム ドライバー属性用の (複合) 値を返します。 エラーが発生した場合は NULL を返します。  
  
## <a name="remarks"></a>Remarks  
例については、「 [PDOStatement::setAttribute](../../connect/php/pdostatement-setattribute.md) 」を参照してください。  
  
PDO のサポートは [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]のバージョン 2.0 で追加されました。  
  
## <a name="see-also"></a>参照  
[PDOStatement クラス](../../connect/php/pdostatement-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
